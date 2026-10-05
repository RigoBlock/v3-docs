# AUniswap

## Overview

#### License: Apache-2.0-or-later

```solidity
contract AUniswap is IAUniswap, IMinimumVersion
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### constructor

```solidity
constructor(address weth)
```


### requiredVersion (0x2ea6c3f0)

```solidity
function requiredVersion() external pure override returns (string memory)
```

Returns the minimum implementation version to use an external application.

Adapters must implement it when modifying proxy state or storage.


Return values:

| Name | Type   | Description                              |
| :--- | :----- | :--------------------------------------- |
| [0]  | string | String of the minimum supported version. |

### unwrapWETH9 (0x49616997)

```solidity
function unwrapWETH9(uint256 amountMinimum) external override
```

Unwraps the contract's WETH9 balance and sends it to recipient as ETH.

The amountMinimum parameter prevents malicious contracts from stealing WETH9 from users.


Parameters:

| Name          | Type    | Description                            |
| :------------ | :------ | :------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap. |

### unwrapWETH9 (0x49404b7c)

```solidity
function unwrapWETH9(uint256 amountMinimum, address) external override
```

Unwraps ETH from WETH9.


Parameters:

| Name          | Type    | Description                                    |
| :------------ | :------ | :--------------------------------------------- |
| amountMinimum | uint256 | The minimum amount of WETH9 to unwrap.         |
| recipient     | address | The address to keep same uniswap npm selector. |

### wrapETH (0x1c58db4f)

```solidity
function wrapETH(uint256 value) external override
```

Wraps ETH.

Client must wrap if input is native currency.


Parameters:

| Name  | Type    | Description                   |
| :---- | :------ | :---------------------------- |
| value | uint256 | The ETH amount to be wrapped. |
