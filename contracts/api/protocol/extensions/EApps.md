# EApps

## Overview

#### License: Apache-2.0-or-later

```solidity
contract EApps is IEApps
```

A universal aggregator for external contracts positions.

External positions are consolidating into a single view contract. As more apps are connected, can be split into multiple mixing.

Future-proof as can route to dedicated extensions, should the size of the contract become too big.
## Errors info

### UnknownApplication

```solidity
error UnknownApplication(uint256 appType)
```


## Functions info

### constructor

```solidity
constructor(EAppsParams memory params)
```

The different immutable addresses will result in different deployed addresses on different networks.


Parameters:

| Name   | Type               | Description                                            |
| :----- | :----------------- | :----------------------------------------------------- |
| params | struct EAppsParams | Chain-specific addresses bundled into a single struct. |

### getAppTokenBalances (0x64397f68)

```solidity
function getAppTokenBalances(
    uint256 packedApplications
) external override returns (ExternalApp[] memory)
```

Uses temporary storage to cache token prices, which can be used in MixinPoolValue.


Parameters:

| Name               | Type    | Description                                                |
| :----------------- | :------ | :--------------------------------------------------------- |
| packedApplications | uint256 | The uint encoded bitmap flags of the active applications.  |


Return values:

| Name        | Type                 | Description                                                        |
| :---------- | :------------------- | :----------------------------------------------------------------- |
| appBalances | struct ExternalApp[] | The arrays of lists of token balances grouped by application type. |

### getUniV4TokenIds (0x0bd692b8)

```solidity
function getUniV4TokenIds()
    external
    view
    override
    returns (uint256[] memory tokenIds)
```

Returns the pool's Uniswap V4 active liquidity positions.


Return values:

| Name     | Type      | Description                            |
| :------- | :-------- | :------------------------------------- |
| tokenIds | uint256[] | Array of liquidity position token ids. |
