# IAUniswap

## Overview

#### License: Apache 2.0

```solidity
interface IAUniswap
```


## Functions info

### unwrapWETH9 (0x49616997)

```solidity
function unwrapWETH9(uint256 amountMinimum) external
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH.

The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users.


Parameters:

| Name          | Type    | Description                            |
| :------------ | :------ | :------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap. |

### unwrapWETH9 (0x49404b7c)

```solidity
function unwrapWETH9(uint256 amountMinimum, address recipient) external
```

Unwraps ETH from WETH9.


Parameters:

| Name          | Type    | Description                                    |
| :------------ | :------ | :--------------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap.         |
| recipient     | address | The address to keep same uniswap npm selector. |

### wrapETH (0x1c58db4f)

```solidity
function wrapETH(uint256 value) external
```

Wraps ETH.

Client must wrap if input is native currency.


Parameters:

| Name  | Type    | Description                   |
| :---- | :------ | :---------------------------- |
| value | uint256 | The ETH amount to be wrapped. |
