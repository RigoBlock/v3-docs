# IRigoblockV3PoolActions

## Overview

#### License: Apache 2.0

```solidity
interface IRigoblockV3PoolActions
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### mint (0x156e29f6)

```solidity
function mint(
    address recipient,
    uint256 amountIn,
    uint256 amountOutMin
) external payable returns (uint256 recipientAmount)
```

Allows a user to mint pool tokens on behalf of an address.


Parameters:

| Name         | Type    | Description                                                          |
| :----------- | :------ | :------------------------------------------------------------------- |
| recipient    | address | Address receiving the tokens.                                        |
| amountIn     | uint256 | Amount of base tokens.                                               |
| amountOutMin | uint256 | Minimum amount to be received, prevents pool operator frontrunning.  |


Return values:

| Name            | Type    | Description                           |
| :-------------- | :------ | :------------------------------------ |
| recipientAmount | uint256 | Number of tokens minted to recipient. |

### burn (0xb390c0ab)

```solidity
function burn(
    uint256 amountIn,
    uint256 amountOutMin
) external returns (uint256 netRevenue)
```

Allows a pool holder to burn pool tokens.


Parameters:

| Name         | Type    | Description                                                          |
| :----------- | :------ | :------------------------------------------------------------------- |
| amountIn     | uint256 | Number of tokens to burn.                                            |
| amountOutMin | uint256 | Minimum amount to be received, prevents pool operator frontrunning.  |


Return values:

| Name       | Type    | Description                      |
| :--------- | :------ | :------------------------------- |
| netRevenue | uint256 | Net amount of burnt pool tokens. |
