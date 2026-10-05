# GmxCallbackLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library GmxCallbackLib
```


## Structs info

### ClaimableCollateralInfo

```solidity
struct ClaimableCollateralInfo {
	address token;
	address market;
	uint256 timeKey;
}
```

Metadata for a recorded claimable-collateral DataStore key.
### GmxCallbackSlot

```solidity
struct GmxCallbackSlot {
	Bytes32Set trackedMarkets;
	Bytes32Set claimableCollateralKeys;
	mapping(bytes32 => GmxCallbackLib.ClaimableCollateralInfo) claimableCollateralInfo;
}
```

Storage layout for the GMX callback extension.
## Errors info

### InvalidCallbackAccount

```solidity
error InvalidCallbackAccount()
```


## Functions info

### gmxCallbackData

```solidity
function gmxCallbackData()
    internal
    pure
    returns (GmxCallbackLib.GmxCallbackSlot storage s)
```

Returns the GMX callback storage slot for the current pool.
### addTrackedMarket

```solidity
function addTrackedMarket(address market) internal
```

Adds `market` to the tracked-markets set.
### removeTrackedMarket

```solidity
function removeTrackedMarket(address market) internal
```

Removes `market` from the tracked-markets set.
### containsTrackedMarket

```solidity
function containsTrackedMarket(address market) internal view returns (bool)
```

Returns true when `market` is in the tracked-markets set.
### trackedMarketsCount

```solidity
function trackedMarketsCount() internal view returns (uint256)
```

Returns the number of tracked markets.
### trackedMarketAt

```solidity
function trackedMarketAt(uint256 index) internal view returns (address)
```

Returns the tracked market at `index`.
### removeClaimableCollateralKey

```solidity
function removeClaimableCollateralKey(bytes32 key) internal
```

Removes a fully-claimed collateral key from the tracked set and metadata map.