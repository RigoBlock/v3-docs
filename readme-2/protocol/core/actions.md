# actions

## MixinActions

### nonReentrant

```solidity
modifier nonReentrant()
```

Functions with this modifer cannot be reentered. The mutex will be locked before function execution and unlocked after.

### mint

```solidity
function mint(address recipient, uint256 amountIn, uint256 amountOutMin) public payable returns (uint256 recipientAmount)
```

Allows a user to mint pool tokens on behalf of an address.

#### Parameters

| Name         | Type    | Description                                                         |
| ------------ | ------- | ------------------------------------------------------------------- |
| recipient    | address | Address receiving the tokens.                                       |
| amountIn     | uint256 | Amount of base tokens.                                              |
| amountOutMin | uint256 | Minimum amount to be received, prevents pool operator frontrunning. |

#### Return Values

| Name            | Type    | Description                           |
| --------------- | ------- | ------------------------------------- |
| recipientAmount | uint256 | Number of tokens minted to recipient. |

### burn

```solidity
function burn(uint256 amountIn, uint256 amountOutMin) external returns (uint256 netRevenue)
```

Allows a pool holder to burn pool tokens.

#### Parameters

| Name         | Type    | Description                                                         |
| ------------ | ------- | ------------------------------------------------------------------- |
| amountIn     | uint256 | Number of tokens to burn.                                           |
| amountOutMin | uint256 | Minimum amount to be received, prevents pool operator frontrunning. |

#### Return Values

| Name       | Type    | Description                      |
| ---------- | ------- | -------------------------------- |
| netRevenue | uint256 | Net amount of burnt pool tokens. |

### decimals

```solidity
function decimals() public view virtual returns (uint8)
```

Returns token decimals.

#### Return Values

| Name | Type  | Description               |
| ---- | ----- | ------------------------- |
| \[0] | uint8 | Uint8 number of decimals. |

### \_getFeeCollector

```solidity
function _getFeeCollector() internal view virtual returns (address)
```

### \_getMinPeriod

```solidity
function _getMinPeriod() internal view virtual returns (uint48)
```

### \_getSpread

```solidity
function _getSpread() internal view virtual returns (uint16)
```

### \_getUnitaryValue

```solidity
function _getUnitaryValue() internal view virtual returns (uint256)
```

### \_allocateMintTokens

```solidity
function _allocateMintTokens(address recipient, uint256 mintedAmount) private returns (uint256 recipientAmount)
```

Allocates tokens to recipient. Fee tokens are locked too.

_Each new mint on same recipient sets new activation on all owned tokens._

#### Parameters

| Name         | Type    | Description               |
| ------------ | ------- | ------------------------- |
| recipient    | address | Address of the recipient. |
| mintedAmount | uint256 | Value of issued tokens.   |

#### Return Values

| Name            | Type    | Description                               |
| --------------- | ------- | ----------------------------------------- |
| recipientAmount | uint256 | Number of new tokens issued to recipient. |

### \_allocateBurnTokens

```solidity
function _allocateBurnTokens(uint256 amountIn) private returns (uint256 burntAmount)
```

Destroys tokens of holder.

_Fee is paid in pool tokens._

#### Parameters

| Name     | Type    | Description                  |
| -------- | ------- | ---------------------------- |
| amountIn | uint256 | Value of tokens to be burnt. |

#### Return Values

| Name        | Type    | Description                 |
| ----------- | ------- | --------------------------- |
| burntAmount | uint256 | Number of net burnt tokens. |

### \_assertBiggerThanMinimum

```solidity
function _assertBiggerThanMinimum(uint256 amount) private view
```

### \_safeTransfer

```solidity
function _safeTransfer(address to, uint256 amount) private
```

### \_safeTransferFrom

```solidity
function _safeTransferFrom(address from, address to, uint256 amount) private
```
