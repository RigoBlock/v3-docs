# GmxLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library GmxLib
```

NAV-only GMX v2 helpers. Keeps the adapter surface out of the NAV
code path so `ENavView` / `EApps` stay as small as possible.
## Structs info

### TokenPrice

```solidity
struct TokenPrice {
	address token;
	Price.Props price;
}
```


## Functions info

### getGmxPositionBalances

```solidity
function getGmxPositionBalances(
    address account
) internal view returns (AppTokenBalance[] memory balances)
```


### getGmxPrice

```solidity
function getGmxPrice(
    address token
) internal view returns (Price.Props memory price)
```

Returns the best available GMX price for `token`.

Tries the GMX Chainlink price provider first, falls back to a hardcoded Chainlink aggregator.
Returns a zero Price.Props when the token cannot be priced or the fallback is stale/invalid.