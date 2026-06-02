---
description: Oracle-protected Swaps
---

# Swap Shield

Rigoblock offers oracle-protected swaps. Every quote is compared against an oracle price and the API returns the deviation from said price. Integrators can inspect the reponse, and decide whether the quote should be executed or not. When a price feed is not available for the target token pair, a `false` boolean is returned alongside a null `oracleAmount`.&#x20;

The trader.rigoblock.com agent blocks rogue swaps via the Swap Shield - a component outside of control of the agent that reverts any trade that is 5% off the oracle price. It is the first line of defense in Rigoblock’s two-layer agent safety stack and is enabled by default on every trade.

### How Swap Shield Works

Before any swap calldata is built or broadcast the system automatically compares the received DEX quote against the onchain BackGeoOracle price.

The trade is instantly blocked if the DEX quote deviates more than 5 percent in either direction from the oracle price. This unified two-sided tolerance means:

* More than 5 percent worse than oracle → protects against bad fills, low liquidity, or stale DEX state
* More than 5 percent better than oracle → protects against manipulation, front-running, or stale oracle routes

If the oracle returns NO\_PRICE\_FEED for a token Swap Shield gracefully allows the swap. This is reserved for legitimate actions such as selling airdrops or tokens received via direct transfer. Otherwise, tokens held by the Rigoblock smart pools are guaranteed to have a price feed.

Swap Shield operates completely separately from your configurable slippage tolerance which you can still set between 0.1 percent and 50 percent.

### Key Benefits&#xD;

* Prevents execution at clearly unfavorable prices
* Works identically for manual chat commands TWAP slices and fully autonomous agents
* Mandatory for scoped delegation — cannot be bypassed without explicit temporary opt-out
* Fully open-source and verifiable in the agentic-operator repository
* Cannot be modified or disabled by the agent

### Configuration and Tools

* Enabled by default on all vaults using the AI Agent
* Temporary override the default tolerance for 10 minutes. During this window you can override the parameter up to 50 percent if needed. The shield automatically re-enables after the TTL.
* Monitoring shield status and events are visible directly in the agent chat and via Telegram notifications.

### Activation Scope&#xD;

Swap Shield activates on:

* every manual swap command
* every TWAP slice
* every trade executed via the x402 API

It always runs before NAV Shield slippage checks and the 7-point execution validation.

### See also

NAV Shield\
[TWAP Order](twap-order.md)\
[Code repository on GitHub](https://github.com/RigoBlock/agentic-operator)

Try it now at [trader.rigoblock.com](https://trader.rigoblock.com)
