# MixinActions

## Overview

#### License: Apache 2.0-or-later

```solidity
abstract contract MixinActions is MixinStorage, ReentrancyGuardTransient
```


## Errors info

### BaseTokenBalance

```solidity
error BaseTokenBalance()
```


### NativeCurrencyNotAccepted

```solidity
error NativeCurrencyNotAccepted()
```


### PoolAmountSmallerThanMinimum

```solidity
error PoolAmountSmallerThanMinimum(uint16 minimumOrderDivisor)
```


### PoolBurnNotEnough

```solidity
error PoolBurnNotEnough()
```


### PoolBurnNullAmount

```solidity
error PoolBurnNullAmount()
```


### PoolBurnOutputAmount

```solidity
error PoolBurnOutputAmount()
```


### PoolCallerNotWhitelisted

```solidity
error PoolCallerNotWhitelisted()
```


### PoolMinimumPeriodNotEnough

```solidity
error PoolMinimumPeriodNotEnough()
```


### PoolMintAmountIn

```solidity
error PoolMintAmountIn()
```


### PoolMintInvalidRecipient

```solidity
error PoolMintInvalidRecipient()
```


### PoolMintOutputAmount

```solidity
error PoolMintOutputAmount()
```


### PoolTokenNotActive

```solidity
error PoolTokenNotActive()
```


### InvalidOperator

```solidity
error InvalidOperator()
```


### PoolMintTokenNotActive

```solidity
error PoolMintTokenNotActive()
```


### NonFractionable

```solidity
error NonFractionable()
```


## Functions info

### mint (0x156e29f6)

```solidity
function mint(
    address recipient,
    uint256 amountIn,
    uint256 amountOutMin
) external payable override nonReentrant returns (uint256 recipientAmount)
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

### mintWithToken (0xf7b94b33)

```solidity
function mintWithToken(
    address recipient,
    uint256 amountIn,
    uint256 amountOutMin,
    address tokenIn
) external payable override nonReentrant returns (uint256 recipientAmount)
```

Allows a user to mint pool tokens on behalf of an address using a desired token.

The token must be vault-owned, i.e. in the active token list, after operator action.


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
) external override nonReentrant returns (uint256 netRevenue)
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

### burnForToken (0x78b3dea4)

```solidity
function burnForToken(
    uint256 amountIn,
    uint256 amountOutMin,
    address tokenOut
) external override nonReentrant returns (uint256 netRevenue)
```

Allows a pool holder to burn pool tokens and receive a token other than base token.

The method is a fallback for when the vault does not hold enough base token, reverts otherwise.


Parameters:

| Name         | Type    | Description                                                          |
| :----------- | :------ | :------------------------------------------------------------------- |
| amountIn     | uint256 | Number of tokens to burn.                                            |
| amountOutMin | uint256 | Minimum amount to be received, prevents pool operator frontrunning.  |
| tokenOut     | address | The token to be received in exchange for pool tokens.                |


Return values:

| Name       | Type    | Description                      |
| :--------- | :------ | :------------------------------- |
| netRevenue | uint256 | Net amount of burnt pool tokens. |

### updateUnitaryValue (0xe7d8724e)

```solidity
function updateUnitaryValue()
    external
    override
    returns (NetAssetsValue memory navParams)
```

Allows anyone to store an up-to-date pool price.

Reentrancy protection provided by calling functions (mint, burn, depositV3, donate)

updateUnitaryValue is the only method explicitly exempt from the Hyperliquid settlement lock

(asserted in the Hyperliquid branch of EApps): it is NAV-neutral, and crosschain donate

routes through it.

Return values:

| Name      | Type                  | Description                                                     |
| :-------- | :-------------------- | :-------------------------------------------------------------- |
| navParams | struct NetAssetsValue | Tuple of unitary value, net total value, net total liabilities. |

### setOperator (0x558a7297)

```solidity
function setOperator(
    address operator,
    bool approved
) external override returns (bool)
```

Sets or removes an operator for the caller.


Parameters:

| Name     | Type    | Description                   |
| :------- | :------ | :---------------------------- |
| operator | address | The address of the operator.  |
| approved | bool    | The approval status.          |


Return values:

| Name | Type | Description        |
| :--- | :--- | :----------------- |
| [0]  | bool | bool True, always. |

### decimals (0x313ce567)

```solidity
function decimals() public view virtual override returns (uint8)
```

Returns the number of decimals of the pool token.


Return values:

| Name | Type  | Description         |
| :--- | :---- | :------------------ |
| [0]  | uint8 | Number of decimals. |

### isOperator (0xb6363cf2)

```solidity
function isOperator(
    address holder,
    address operator
) public view virtual returns (bool approved)
```



Parameters:

| Name     | Type    | Description                   |
| :------- | :------ | :---------------------------- |
| holder   | address | The address of the holder.    |
| operator | address | The address of the operator.  |


Return values:

| Name     | Type | Description          |
| :------- | :--- | :------------------- |
| approved | bool | The approval status. |
