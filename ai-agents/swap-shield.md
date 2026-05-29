# Swap Shield

```markdown
# Swap Shield

Swap Shield is the oracle-based price protection layer that runs at the **AI Trading Agent** and x402 API level (`trader.rigoblock.com`). It protects every swap — whether triggered manually in the chat, via TWAP slices, or by autonomous agents — from bad quotes, poor liquidity, manipulation, or fat-finger errors.

It is the first layer of Rigoblock’s two-layer safety stack (together with NAV Shield) and is enabled by default on all trades.

## How Swap Shield Works

Before any swap calldata is generated or broadcast, the system performs an automatic cross-check:

- The received DEX quote (from 0x Aggregator, Uniswap, or any router) is compared against the vault’s trusted **BackGeoOracle 5-minute TWAP** via the internal call `vault.convertTokenAmount(tokenIn, amountIn, tokenOut)`.
- The trade is **instantly blocked** if:
    - The quote is **> 5% worse** than the oracle price → protects against bad fills, low liquidity, or stale DEX state.
    - The quote is **> 10% better** than the oracle price → protects against potential manipulation, front-running, or oracle-stale attacks.
- If the oracle returns `NO_PRICE_FEED` for a token, the shield gracefully allows the swap (useful for selling airdrops or tokens received via direct transfer).

This check happens at the offchain agent layer and is completely separate from standard slippage protection (which remains configurable at 0.1%–5%).

## Key Benefits

- Prevents users and agents from executing at clearly unfavorable prices.
- Works identically for human chat commands and fully autonomous strategies.
- Open-source and verifiable (see [agentic-operator repo](https://github.com/RigoBlock/agentic-operator)).
- Mandatory by design for scoped delegation — agents cannot bypass it without explicit temporary opt-out.

## Configuration & Tools

- **Enabled by default** on every vault using the AI Agent.
- **Temporary disable**: Use the `disable_swap_shield` tool (10-minute TTL).  
  After the TTL expires, the shield automatically re-enables.  
  Note: Because TWAP slices run on cron (minimum 5 min intervals), disabling affects any slice within the TTL window.
- Operators can monitor shield status and events directly in the agent chat or via Telegram notifications.

## When Swap Shield Activates

- Every manual swap (“swap 10 ETH to USDC”)
- Every TWAP slice
- Every agent-initiated trade via x402 API
- GMX V2 perp openings/closings (when routed through the swap path)

It runs before NAV Shield, slippage, and the 7-point execution validation.

## See also

- [NAV Shield](/ai-agents/nav-shield)
- [TWAP Order](/ai-agents/twap-order)
- [Agentic Operator GitHub](https://github.com/RigoBlock/agentic-operator)

---

**Try it live** → [trader.rigoblock.com](https://trader.rigoblock.com)
```
