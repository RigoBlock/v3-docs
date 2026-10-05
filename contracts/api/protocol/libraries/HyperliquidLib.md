# HyperliquidLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library HyperliquidLib
```

Rigoblock-specific helpers for Hyperliquid NAV and storage.

security-contact: security@rigoblock.com
## Errors info

### NavLocked

```solidity
error NavLocked()
```


## Functions info

### getHyperliquidBalances

```solidity
function getHyperliquidBalances(
    address account
) internal view returns (AppTokenBalance[] memory balances)
```

Returns Hyperliquid balances, adding the in-flight amount only within the same EVM block
as the recorded action. HyperCore processes EVM->Core transfers and CoreWriter actions
immediately after each EVM block is built, so the precompiles reflect them from the next EVM
block on — keeping the in-flight amount any longer would double-count.

Does not enforce the settlement lock: enforcement lives in assertNavUnlocked, asserted from

the Hyperliquid branch of EApps. See docs/hyperliquid/INTEGRATION.md.
### recordAction

```solidity
function recordAction(
    int256 amount,
    bool isSpotSend
) internal returns (uint64 pendingBefore)
```


### assertNavUnlocked

```solidity
function assertNavUnlocked() internal view
```

Reverts while NAV reads may still be stale after a Core deposit/spot-send.

Within the same EVM block, reads are exact for both action types: a deposit's in-flight

amount compensates the not-yet-visible Core credit, and a spot-send has not executed yet

(its destination is always the pool's own address, so it is NAV-neutral at every stage).

From the next EVM block on, in-flight is dropped; the precompiles normally reflect the

action by then (transfers are processed right after each EVM block), but delayed actions

and sequencing edge cases are covered by the time lock on top.

Asserted from the Hyperliquid branch of EApps, which every NAV write reaches.