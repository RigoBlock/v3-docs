# IEApps

## Overview

#### License: Apache 2.0

```solidity
interface IEApps
```


## Functions info

### getAppTokenBalances (0x64397f68)

```solidity
function getAppTokenBalances(
    uint256 packedApplications
) external returns (ExternalApp[] memory appBalances)
```

Returns token balances owned in a set of external contracts.


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
function getUniV4TokenIds() external view returns (uint256[] memory tokenIds)
```

Returns the pool's Uniswap V4 active liquidity positions.


Return values:

| Name     | Type      | Description                            |
| :------- | :-------- | :------------------------------------- |
| tokenIds | uint256[] | Array of liquidity position token ids. |
