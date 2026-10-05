# GmxAdapterLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library GmxAdapterLib
```


## Errors info

### MaxGmxPositionsReached

```solidity
error MaxGmxPositionsReached()
```


### GmxRouterNotAuthorized

```solidity
error GmxRouterNotAuthorized()
```


## Functions info

### assertRouterAuthorized

```solidity
function assertRouterAuthorized() internal view
```

Reverts if the GMX ExchangeRouter lost the CONTROLLER role (e.g. after a GMX
contract rotation), which would make order writes and claims revert downstream.
### computeExecutionFee

```solidity
function computeExecutionFee(
    bool isIncrease,
    uint256 callbackGasLimit
) internal view returns (uint256)
```


### getMarketTokens

```solidity
function getMarketTokens(
    address market
) internal view returns (address longToken, address shortToken)
```


### getMarketIndexToken

```solidity
function getMarketIndexToken(address market) internal view returns (address)
```


### isIndexTokenPriced

```solidity
function isIndexTokenPriced(address token) internal view returns (bool)
```


### assertPositionLimitNotReached

```solidity
function assertPositionLimitNotReached(
    address account,
    address market,
    address collateralToken,
    bool isLong
) internal view
```


### isMarketActive

```solidity
function isMarketActive(
    address account,
    address market
) internal view returns (bool)
```


### hasClaimableFundingFees

```solidity
function hasClaimableFundingFees(
    address account,
    address market
) internal view returns (bool)
```


### claimableCollateralAmount

```solidity
function claimableCollateralAmount(
    bytes32 amountKey,
    address account
) internal view returns (uint256)
```

