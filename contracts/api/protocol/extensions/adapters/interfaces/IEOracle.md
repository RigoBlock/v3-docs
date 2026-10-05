# IEOracle

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IEOracle
```


## Functions info

### convertBatchTokenAmounts (0x80d13ffa)

```solidity
function convertBatchTokenAmounts(
    address[] calldata tokens,
    int256[] calldata amounts,
    address targetToken
) external view returns (int256 totalConvertedAmount)
```

Returns the sum of the token amounts converted to a target token.

Will first try to convert via cross with chain currency, fallback to direct cross if not available.


Parameters:

| Name        | Type      | Description                                    |
| :---------- | :-------- | :--------------------------------------------- |
| tokens      | address[] | The array of token addresses to be converted.  |
| amounts     | int256[]  | The array of amounts to be converted.          |
| targetToken | address   | The address of the target token.               |


Return values:

| Name                 | Type   | Description                                                 |
| :------------------- | :----- | :---------------------------------------------------------- |
| totalConvertedAmount | int256 | The total value of converted amount in target token amount. |

### convertTokenAmount (0xda0532fb)

```solidity
function convertTokenAmount(
    address token,
    int256 amount,
    address targetToken
) external view returns (int256 convertedAmount)
```

Returns a token amount converted to a target token.

Will first try to convert via cross with chain currency, fallback to direct cross if not available.


Parameters:

| Name        | Type    | Description                                |
| :---------- | :------ | :----------------------------------------- |
| token       | address | The address of the token to be converted.  |
| amount      | int256  | The amount to be converted.                |
| targetToken | address | The address of the target token.           |


Return values:

| Name            | Type   | Description                                           |
| :-------------- | :----- | :---------------------------------------------------- |
| convertedAmount | int256 | The value of converted amount in target token amount. |

### hasPriceFeed (0x0b7983a2)

```solidity
function hasPriceFeed(address token) external view returns (bool)
```

Returns whether a token has a price feed.


Parameters:

| Name  | Type    | Description                |
| :---- | :------ | :------------------------- |
| token | address | The address of the token.  |


Return values:

| Name | Type | Description                    |
| :--- | :--- | :----------------------------- |
| [0]  | bool | Boolean the price feed exists. |

### getTwap (0x3d47d227)

```solidity
function getTwap(address token) external view returns (int24 twap)
```

Returns token price aginst native currency.


Parameters:

| Name  | Type    | Description                |
| :---- | :------ | :------------------------- |
| token | address | The address of the token.  |


Return values:

| Name | Type  | Description                      |
| :--- | :---- | :------------------------------- |
| twap | int24 | The time weighted average price. |
