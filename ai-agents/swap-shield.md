# Swap Shield

```markdown
# Swap Shield

Swap Shield is the oracle-based price protection layer that runs at the AI Trading Agent level (`trader.rigoblock.com`) and x402 API. It is the first line of defense in Rigoblock’s two-layer agent safety stack and is enabled by default on every trade.

## How Swap Shield Works

Before any swap calldata is built or broadcast, the system automatically compares the received DEX quote against the vault’s trusted on-chain **BackGeoOracle 5-minute TWAP** using the internal call:

`vault.convertTokenAmount(tokenIn, amountIn, tokenOut)`

The trade is instantly blocked if one of the following conditions is met:

- The DEX quote is **> 5% worse** than the oracle price (protects against bad fills, low liquidity, or stale DEX state)
- The DEX quote is **> 10% better** than the oracle price (protects against manipulation, front-running, or stale oracle routes)

If the oracle returns `NO_PRICE_FEED` for a token, Swap Shield gracefully allows the swap. This case is reserved for legitimate actions such as selling airdrops or tokens received via direct transfer.

Swap Shield operates completely separately from standard slippage tolerance (which you can still configure between 0.1%–5%).

## Key Benefits

- Prevents execution at clearly unfavorable prices
- Works identically for manual chat commands, TWAP slices, and fully autonomous agents
- Mandatory for scoped delegation — cannot be bypassed without explicit temporary opt-out
- Fully open-source (see agentic-operator repository)

## Configuration & Tools

- Enabled by default on all vaults using the AI Agent
- Temporary disable: call the `disable_swap_shield` tool (valid for 10 minutes). The shield automatically re-enables after the TTL.
- Monitoring: shield status and events are visible directly in the agent chat and via Telegram notifications

## Activation Scope

Swap Shield activates on:
- Every manual swap command
- Every TWAP slice
- Every trade executed via the x402 API
- GMX V2 perp open/close actions (when routed through swap path)

It always runs before NAV Shield, slippage checks, and the 7-point execution validation.

## See also

- [NAV Shield](/ai-agents/nav-shield)
- [TWAP Order](/ai-agents/twap-order)
- [FAQ – What is the Swap Shield?](https://rigoblock.com/faq.html)

---

**Try it now** → [trader.rigoblock.com](https://trader.rigoblock.com)
```
