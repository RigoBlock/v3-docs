# TWAP Order

## TWAP Orders — Technical Specification

> This document describes the TWAP (Time-Weighted Average Price) order system built into the Rigoblock Agentic Operator. It covers the data model, execution pipeline, safety controls, and API surface for integrators interested in building on top of or integrating with TWAP execution.

***

### What Is a TWAP Order?

A TWAP order splits a large swap into **N equal-sized slices** executed at **regular time intervals**. The goal is to reduce price impact on the DEX by spreading the trade over time rather than executing it as a single atomic swap.

A TWAP order:

* Executes deterministically — no LLM judgment in the execution loop
* Runs autonomously on a cron schedule (minimum 5-minute intervals)
* Has a defined total amount, slice size, and duration
* Supports both **buy-side** (exact-output) and **sell-side** (exact-input) semantics

**Example:**

> "Buy 100 GRG with ETH, 20 per slice, every 5 minutes"
>
> → 5 slices × 20 GRG (exact-output) × 5-minute interval = completes in 25 minutes

***

### How TWAP Orders Work

#### Lifecycle

```
create_twap_order
      │
      ▼
  KV store (twap:{vault})
      │
      ▼  [every cron tick, ≥5 min]
  runDueTwapOrders()
      │
      ├── is order due? (elapsed + jitter > intervalMinutes * 60_000)
      │        │
      │       Yes
      │        ▼
      │   executeToolCall("build_vault_swap", {tokenIn, tokenOut, amount, dex, chain})
      │        │
      │        ├── Swap Shield check (oracle price vs DEX quote)
      │        ├── NAV shield pre-check (simulate: will NAV drop >10%?)
      │        │
      │   [autoExecute=true]       [autoExecute=false]
      │        │                         │
      │   executeTxList()          Telegram notification
      │        │                   (no on-chain execution)
      │   NAV shield broadcast check
      │   (7-point validation + gas check)
      │        │
      │   CDP signs + broadcasts
      │        │
      │   record TwapEvent
      │   notify Telegram
      │        │
      ▼   order.slicesExecuted++
  save updated order state
```

***

### Data Model

```typescript
interface TwapOrder {
  id: number;                // Monotonically increasing per vault (high-water-mark, never reused)
  side: "buy" | "sell";     // "buy" = totalAmount in buyToken; "sell" = totalAmount in sellToken
  sellToken: string;         // Token symbol or address (user input)
  buyToken: string;          // Token symbol or address (user input)
  sellTokenAddress?: string; // Resolved contract address (set at creation time)
  buyTokenAddress?: string;  // Resolved contract address (set at creation time)
  totalAmount: string;       // Total amount of `side` token (human-readable, 6 decimal precision)
  sliceAmount: string;       // Amount per slice (same denomination as totalAmount)
  sliceCount: number;        // Total planned slices
  intervalMinutes: number;   // Minutes between slices (≥5)
  dex: string;               // Target DEX
  chainId: number;           // EVM chain ID
  vaultAddress: string;      // Rigoblock vault address (lowercase)
  operatorAddress: string;   // Vault owner address (who authorized the order)
  active: boolean;           // false = completed or cancelled
  createdAt: number;         // Unix ms timestamp
  lastExecution?: number;    // Unix ms of last successful or failed slice attempt
  consecutiveFailures: number; // Resets to 0 on success; order pauses at 3
  lastError?: string;        // Last error message (sanitized)
  completedAt?: number;      // Unix ms when all slices executed or order cancelled
  amountSpent: string;       // Running total of sellToken spent
  totalBought: string;       // Running total of buyToken received
  slicesExecuted: number;    // Count of successfully executed slices
  autoExecute: boolean;      // true = auto-broadcast; false = notify only
}
```

#### swapMeta — Slice Fill Data

When a slice executes, the `build_vault_swap` tool returns an `UnsignedTransaction` that includes a `swapMeta` object. The TWAP executor reads this to update the order's accounting fields (`amountSpent`, `totalBought`):

```typescript
interface SwapMeta {
  sellAmount: string;  // Actual (or estimated) sell amount in human-readable units
  sellToken: string;   // Sell token symbol or address
  buyAmount: string;   // Actual (or estimated) buy amount in human-readable units
  buyToken: string;    // Buy token symbol or address
  price: string;       // Human-readable price ratio: "1 ETH = 2079.54 USDC"
  dex: string;         // Target DEX
}
```

If the TWAP executor cannot read `swapMeta` from the returned transaction (e.g., the tool returned an error), the slice failure is recorded but `amountSpent` and `totalBought` are not updated for that slice.

````

### Key Invariants

- `id` is assigned from a **per-vault high-water-mark** stored in KV (`twap-hwm:{vault}`).
  Pruning closed orders never causes ID reuse.
- Maximum **3 active orders per vault**.
- Closed orders (inactive) are pruned to 20 per vault to limit KV growth.
- `slicesExecuted + 1` = the slice number for the next execution.

---

## Token Address Resolution

Token addresses are resolved **at order creation time** using the CoinGecko-backed
token resolver (`src/services/tokenResolver.ts`). The resolved addresses are stored
in `sellTokenAddress` and `buyTokenAddress`.

This ensures:
- **Fail-fast** — if the token doesn't exist on the target chain, the order is
  rejected at creation rather than at cron execution time.
- **Cron independence** — TWAP slices use the stored addresses directly, never
  requiring CoinGecko at execution time (avoids transient resolver failures).

If the user passes a contract address instead of a symbol, it is used as-is.

---

## Execution Pipeline (Per Slice)

Each slice calls `executeToolCall(env, ctx, "build_vault_swap", toolArgs)` with:

```typescript
const toolArgs = side === "buy"
  ? { tokenOut: buyRef, tokenIn: sellRef, amountOut: order.sliceAmount, dex: order.dex }
  : { tokenIn: sellRef, tokenOut: buyRef, amountIn: order.sliceAmount, dex: order.dex };
toolArgs.chain = chainName;
````

This is **identical** to the standard swap tool call path — it goes through the same safety stack as a manually triggered swap.

#### Safety Controls Applied on Every TWAP Slice

**1. Swap Shield (Oracle Price Protection)**

Before building swap calldata, the system compares the DEX quote against the vault's on-chain BackgeoOracle price:

* Blocks if DEX quote is **>5% off** than oracle
* Gracefully allows the swap when the oracle has no price feed for a token (`NO_PRICE_FEED`) within vaults, this case only allows selling non-tracked tokens (i.e. airdrops or direct transfers).

This greatly limits TWAP orders from executing at unfavorable prices due to poor liquidity, stale DEX state, or oracle manipulation.

**2. NAV Shield Pre-Check**

Before the slice transaction is built and returned, the system atomically simulates:

```
multicall([swap_calldata, updateUnitaryValue()])
```

If the simulated post-swap NAV drops **>10%** versus the pre-swap NAV (or the 24-hour baseline, whichever is higher), the slice is **blocked** and an error is recorded.

**3. NAV Shield at Broadcast Time (auto-execute mode)**

For `autoExecute: true`, a second NAV shield check runs inside `executeTxList()` immediately before the CDP-signed transaction is broadcast. This is a belt-and-suspenders check in case market conditions changed between building and broadcasting the calldata.

**4. Seven-Point Execution Validation**

For `autoExecute: true`, `executeTxList()` runs the full 7-point validation:

1. Delegation config exists and is enabled in KV
2. Transaction target == vault address (prevents cross-contract attacks)
3. Function selector is in the allowed whitelist
4. Agent wallet identity matches stored config
5. `eth_call` simulation passes (pre-broadcast revert check)
6. Agent wallet has sufficient ETH for gas - unless sponsored transaction
7. Gas fees within per-chain hard caps

**5. Slippage Protection**

Default slippage: **1% (100 bps)**. Configurable by the operator via:

* `set_default_slippage` tool (persisted per operator in KV)
* `slippageBps` field in the chat request body

Clamped to \[10, 500] bps (0.1%–5%). The LLM cannot set slippage directly.

**6. Auto-Pause on Failure**

After **3 consecutive slice failures**, the order is automatically paused (`active = false`). The operator is notified via Telegram on every failure (not just on auto-pause).

***

### Execution Context

When a TWAP slice fires at cron time, the request context is:

```typescript
const ctx: RequestContext = {
  vaultAddress: order.vaultAddress,
  chainId: order.chainId,
  operatorAddress: order.operatorAddress,
  isBrowserRequest: false,      // allows building unsigned calldata without browser auth
  executionMode: order.autoExecute ? "delegated" : "manual",
};
```

`isBrowserRequest: false` bypasses the browser auth gate (which requires a connected wallet), since TWAP slices run server-side without a browser session. Security is maintained via delegation verification in the execution pipeline.

***

### Manual vs Autonomous Mode

| Mode           | `autoExecute`     | Behavior                                                                        |
| -------------- | ----------------- | ------------------------------------------------------------------------------- |
| **Manual**     | `false` (default) | LLM analyzes + builds tx, sends Telegram notification. No on-chain execution.   |
| **Autonomous** | `true`            | Builds tx + broadcasts via CDP agent wallet. Operator notified after execution. |

Both modes apply the Swap Shield and NAV pre-check when building the transaction. Only autonomous mode applies the broadcast-time NAV check and 7-point validation.

For autonomous mode, the vault must have **active delegation** to the agent wallet on the target chain, with the `execute()` selector included.

***

### KV Storage Schema

| Key                   | Value                                                  | TTL  |
| --------------------- | ------------------------------------------------------ | ---- |
| `twap:{vault}`        | JSON array of `TwapOrder[]` (active + up to 20 closed) | none |
| `twap-hwm:{vault}`    | Highest ID ever assigned (integer string)              | none |
| `twap-events:{vault}` | JSON array of `TwapEvent[]` (last 20 events)           | 24h  |

#### TwapEvent Schema

```typescript
interface TwapEvent {
  orderId: number;
  timestamp: number;    // Unix ms
  sliceNumber: number;  // 1-indexed
  totalSlices: number;
  sellAmount: string;   // Actual amount sold (from swapMeta)
  buyAmount: string;    // Actual amount received (from swapMeta)
  success: boolean;
  error?: string;       // Present on failure (truncated to 400 chars)
}
```

Events are served via `GET /api/strategy-events?vault=0x…&since={timestamp}` and polled by the frontend to show slice history.

***

### API Tools

TWAP orders are created and managed via the `/api/chat` endpoint using the following tools:

#### `create_twap_order`

```json
{
  "side": "buy" | "sell",
  "sellToken": "ETH",
  "buyToken": "GRG",
  "totalAmount": "100",
  "sliceAmount": "20",        // or sliceCount or durationMinutes
  "intervalMinutes": 5,
  "dex": "0x" | "uniswap",
  "chain": "base",
  "autoExecute": true
}
```

**Returns:** Confirmation message with order ID, duration, and mode.

#### `cancel_twap_order`

```json
{ "id": 3 }          // cancel specific order
{ "id": 0 }          // cancel all active orders
```

#### `list_twap_orders`

No parameters. Returns formatted list of all orders (active and closed) with progress, amounts spent, and status.

**Alias:** `list_strategies` maps to the same handler — both names work interchangeably in the chat interface.

***

### Fast-Path Processing

The chat agent includes a **regex-based fast path** for commonly phrased TWAP commands. When a message matches the fast path, the TWAP order is created directly without invoking the LLM — reducing latency and cost.

The fast path activates when the message contains both:

* `"every N minutes"` — sets `intervalMinutes`
* `"X at a time"` — sets `sliceAmount`

Examples that hit the fast path:

```
"Sell 1 ETH for USDC, 0.2 at a time, every 10 minutes"
"Buy 100 GRG with ETH, 20 at a time, every 5 minutes, auto-execute"
```

If neither pattern is present, the full inference path handles the request. The LLM is always invoked for ambiguous phrasing, multi-step requests, or when the user asks follow-up questions about an order.

The fast path also handles:

* `"list twap orders"` / `"list strategies"` → `list_twap_orders`
* `"cancel twap {id}"` / `"cancel all twap orders"` → `cancel_twap_order`
* `"enable/disable swap shield"` → `enable_swap_shield` / `disable_swap_shield`

***

### Constraints

| Constraint                                 | Value                   |
| ------------------------------------------ | ----------------------- |
| Max active orders per vault                | 3                       |
| Max stored closed orders per vault         | 20                      |
| Minimum interval                           | 5 minutes               |
| Max consecutive failures before auto-pause | 3                       |
| Max stored events                          | 20 (per vault, 24h TTL) |

***

### Delegation Requirements (Autonomous Mode)

For `autoExecute: true`, the vault must have **active on-chain delegation** to the agent wallet for each function selector the TWAP executor will call.

#### How Rigoblock Delegation Works

Rigoblock vaults implement a **granular per-selector delegation system**. The vault contract maintains a permission mapping:

```
delegation().selectorToAddressPosition[bytes4 selector][address agent] → bool
```

When a call arrives at the vault's fallback, the contract checks this mapping before forwarding the call to the appropriate adapter. If the calling address is not delegated for that selector, the call reverts.

The operator grants permissions by sending an `updateDelegation(Delegation[])` transaction from their EOA (the vault owner address):

```solidity
struct Delegation {
    address delegated;   // the agent wallet address
    bytes4 selector;     // the function selector to permit
    bool isDelegated;    // true to grant, false to revoke
}
```

Revocation is atomic: `revokeAllDelegations(agentAddress)` removes all selectors for the agent in a single call.

#### Setting Up Delegation

Via the chat interface (browser or API):

```
"Set up delegation on Base"
```

Or programmatically:

```
POST /api/delegation/setup   →  unsigned updateDelegation() tx
  [operator signs + broadcasts]
POST /api/delegation/confirm →  stores delegation state in KV
```

The operator can revoke all permissions instantly at any time:

```
"Revoke delegation on Base"
```

Or on-chain: `pool.revokeAllDelegations(agentAddress)`.

#### EIP-7702 — Code Delegation (Pectra)

EIP-7702, introduced in Ethereum's Pectra upgrade, allows an **EOA to temporarily adopt smart contract code** within a single transaction. It is designed for smart-wallet use cases: a user's EOA can batch calls, pay gas in ERC-20 tokens, or execute sponsored transactions by delegating to a chosen implementation contract for the duration of one transaction.

**TWAP does not use EIP-7702.** The agent wallet is a CDP-managed EOA with its own signing capability — it does not need to adopt smart contract code. The delegation problem TWAP solves is different: it is not "allow this EOA to batch-call during one transaction" but rather "allow this external EOA to call specific vault functions indefinitely, until the operator revokes." That is a **persistent, contract-level** permission that EIP-7702 (which is transaction-scoped and EOA-level) cannot express.

#### EIP-7715 — Scoped Wallet Permissions (`wallet_grantPermissions`)

EIP-7715 proposes a wallet RPC method (`wallet_grantPermissions`) for granting **scoped permissions** to dApps or agents — specifying which functions they may call, with which parameters, and under which conditions (spend limits, expiry, allowed contracts). This is the EIP that most closely resembles Rigoblock's delegation model.

**Conceptual alignment:**

* Both are selector-scoped (specific `bytes4` function signatures)
* Both are address-bound (permission granted to a specific agent address)
* Both support revocation

**Key difference in layer:**

* EIP-7715 operates at the **wallet level** — the permission is enforced by the user's wallet before it signs any transaction.
* Rigoblock delegation operates at the **vault contract level** — the permission is enforced on-chain inside the vault's fallback function, independent of who signs or how.

As EIP-7715 matures, an operator could use it to further constrain what the agent's wallet is permitted to sign (e.g., only transactions targeting this specific vault), complementing the existing on-chain vault delegation. The two layers are not mutually exclusive — vault-level delegation remains the primary enforcement layer.

***

### EIPs and Standards Used

#### EIP-191: Signed Data Standard

Used for **operator authentication**. When setting up TWAP orders via the chat or API, the operator must sign:

```
Welcome to Rigoblock Operator

Sign this message to verify your wallet and access your smart pool assistant.
```

The signature is verified server-side via `viem.verifyMessage()`. Valid for 24 hours. Purpose: proves the caller owns the vault operator wallet, not just the x402 payer wallet.

#### EIP-712: Typed Structured Data Hashing (implicit)

The Rigoblock vault's `updateDelegation()` function uses typed structs:

```solidity
struct Delegation {
    address delegated;
    bytes4 selector;
    bool isDelegated;
}
```

When the operator sets up delegation, they sign and send `updateDelegation(Delegation[])` from their EOA. This grants the agent wallet selector-level permissions.

#### EIP-1193: Ethereum Provider JavaScript API

The TWAP creation flow runs inside the chat agent. Actual slice execution (for autonomous mode) uses the **CDP Server Wallet** (Coinbase Developer Platform). CDP manages the agent's private key server-side in a TEE (Trusted Execution Environment) — the key never appears in Worker code or KV storage. The CDP account is wrapped into a viem-compatible `EvmServerAccount` / `LocalAccount` interface for signing.

For manual mode, the slice transaction is returned as unsigned calldata (same as all other vault transactions) and the operator signs it via their connected wallet using the standard `eth_sendTransaction` call.

#### x402: HTTP Micropayments (RFC Draft)

TWAP orders are created via the `/api/chat` endpoint, which is x402-gated at **$0.015 USDC per request** (paid on Base mainnet). The x402 payment is an **API access fee** — it does NOT authorize vault operations. Vault authorization requires a separate operator signature (EIP-191) AND active on-chain delegation. These are completely independent layers: a request may have x402 payment without operator auth (anonymous mode, receives unsigned calldata only) or both (full access including delegated execution).

See AGENTS.md for full x402 setup instructions.

***

### Observability

#### Telegram Notifications

If Telegram is paired (`/api/telegram/pair`), the operator receives:

* **Per-slice execution** (autonomous mode): swap amounts, progress fraction, tx link
* **Order completion**: total spent/bought summary
* **Slice failure**: error message + Tenderly debug calldata (to/from/value/data)
* **Auto-pause**: notification when 3 consecutive failures occur

#### Strategy Events Polling

```
GET /api/strategy-events?vault=0xYourVault&since=1700000000000
```

Returns:

```json
{
  "events": [
    {
      "type": "twap",
      "timestamp": 1700000300000,
      "success": true,
      "twapOrderId": 3,
      "summary": "Slice 2/5: 0.042 ETH → 21.3 GRG"
    }
  ]
}
```

***

### Security Properties

TWAP orders cannot:

| Action                             | Reason                                            |
| ---------------------------------- | ------------------------------------------------- |
| Execute without delegation         | Agent wallet only has whitelisted selectors       |
| Execute a swap that drops NAV >10% | NAV shield blocked at build AND broadcast time    |
| Execute at an unfavorable price    | Swap Shield compares against on-chain TWAP oracle |
| Call arbitrary contracts           | Transaction target must equal vault address       |
| Exceed gas caps                    | Hard-coded per-chain gas limits                   |

The vault contract enforces these constraints on-chain, independently of the agent or TWAP scheduler code. Even a compromised Worker cannot bypass the on-chain delegation mapping.

***

### Example: Creating a TWAP Order via x402

```typescript
import { x402Client, x402HTTPClient } from "@x402/core/client";
import { ExactEvmScheme, toClientEvmSigner } from "@x402/evm";
import { createWalletClient, http } from "viem";
import { base } from "viem/chains";
import { privateKeyToAccount } from "viem/accounts";

// 1. Set up x402 payment client (USDC on Base)
const account = privateKeyToAccount(PRIVATE_KEY);
const walletClient = createWalletClient({ account, chain: base, transport: http() });
const signer = toClientEvmSigner(account, walletClient.extend(publicActions));
const client = new x402Client();
client.register("eip155:8453", new ExactEvmScheme(signer));
const httpClient = new x402HTTPClient(client);

// 2. Sign the operator auth message
const authMessage = [
  "Welcome to Rigoblock Operator",
  "",
  "Sign this message to verify your wallet and access your smart pool assistant.",
].join("\n");
const authSignature = await walletClient.signMessage({ message: authMessage });
const authTimestamp = Date.now();

// 3. Create the TWAP order via /api/chat
const res = await fetch("https://trader.rigoblock.com/api/chat");
if (res.status === 402) {
  const paymentPayload = await httpClient.createPaymentPayload(
    httpClient.getPaymentRequiredResponse(name => res.headers.get(name), await res.json())
  );
  const headers = {
    ...httpClient.encodePaymentSignatureHeader(paymentPayload),
    "Content-Type": "application/json",
  };

  const chatRes = await fetch("https://trader.rigoblock.com/api/chat", {
    method: "POST",
    headers,
    body: JSON.stringify({
      messages: [{ role: "user", content: "Buy 100 GRG with ETH, 20 per slice, every 5 minutes, auto-execute" }],
      vaultAddress: "0xYourVaultAddress",
      chainId: 8453,
      operatorAddress: "0xYourOperatorAddress",
      authSignature,
      authTimestamp,
      executionMode: "delegated",
    }),
  });

  const result = await chatRes.json();
  console.log(result.reply);
  // → "✅ TWAP order #1 created! Buy 100 GRG with ETH | 5 slices of ~20.000000 GRG every 5m | Duration: 25 minutes | DEX: 0x | Mode: ⚡ Auto-execute | First slice: next cron tick"
}
```

***

### Direct Tool API (x402)

You can also call the `create_twap_order` tool directly without going through the LLM, using `POST /api/tools/create_twap_order`:

```bash
curl -X POST https://trader.rigoblock.com/api/tools/create_twap_order \
  -H "X-PAYMENT: <x402-payment-header>" \
  -H "Content-Type: application/json" \
  -d '{
    "side": "sell",
    "sellToken": "ETH",
    "buyToken": "USDC",
    "totalAmount": "1",
    "sliceCount": 4,
    "intervalMinutes": 10,
    "dex": "uniswap",
    "chain": "base",
    "autoExecute": true,
    "vaultAddress": "0xYourVault",
    "operatorAddress": "0xYourOperator",
    "authSignature": "0x...",
    "authTimestamp": 1700000000000
  }'
```

***

### Comparison with Strategy System

The Rigoblock Agentic Operator also has a general **strategy system** (LLM-driven) where an LLM evaluates market conditions and decides whether to execute a trade. TWAP orders differ fundamentally:

| Aspect           | TWAP Orders                                 | LLM Strategies                                    |
| ---------------- | ------------------------------------------- | ------------------------------------------------- |
| Execution logic  | Deterministic (always executes on schedule) | LLM judgment (may skip if conditions unfavorable) |
| Tool calls       | Direct tool dispatch (no LLM involved)      | LLM decides what to call                          |
| Latency          | Low (sub-second build time)                 | Higher (LLM inference)                            |
| Cost             | Lower (no LLM tokens on execution)          | Higher (LLM tokens per run)                       |
| Flexibility      | Fixed: swap at regular intervals            | Flexible: any supported operation                 |
| Monitoring       | Per-slice events + Telegram                 | Per-run recommendations + Telegram                |
| Failure handling | Auto-pause at 3 failures                    | Auto-pause at 3 failures                          |

TWAP orders are the right choice for mechanical, scheduled execution. LLM strategies are better for adaptive, market-condition-sensitive execution.
