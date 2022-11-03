# state

## MixinPoolState

### balanceOf

```solidity
function balanceOf(address who) external view returns (uint256)
```

_Returns how many pool tokens a user holds._

#### Parameters

| Name | Type    | Description                    |
| ---- | ------- | ------------------------------ |
| who  | address | Address of the target account. |

#### Return Values

| Name | Type    | Description     |
| ---- | ------- | --------------- |
| \[0] | uint256 | Number of pool. |

### getPoolStorage

```solidity
function getPoolStorage() external view returns (struct IRigoblockV3PoolState.ReturnedPool poolInitParams, struct IRigoblockV3PoolState.PoolParams poolVariables, struct IRigoblockV3PoolState.PoolTokens poolTokensInfo)
```

Returns the aggregate pool generic storage.

#### Return Values

| Name           | Type                                      | Description                           |
| -------------- | ----------------------------------------- | ------------------------------------- |
| poolInitParams | struct IRigoblockV3PoolState.ReturnedPool | The pool's initialization parameters. |
| poolVariables  | struct IRigoblockV3PoolState.PoolParams   | The pool's variables.                 |
| poolTokensInfo | struct IRigoblockV3PoolState.PoolTokens   | The pool's tokens info.               |

### getUserAccount

```solidity
function getUserAccount(address who) external view returns (struct IRigoblockV3PoolState.UserAccount)
```

### owner

```solidity
function owner() external view returns (address)
```

Returns the address of the owner.

#### Return Values

| Name | Type    | Description           |
| ---- | ------- | --------------------- |
| \[0] | address | Address of the owner. |

### decimals

```solidity
function decimals() public view returns (uint8)
```

Decimals are initialized at proxy creation.

#### Return Values

| Name | Type  | Description         |
| ---- | ----- | ------------------- |
| \[0] | uint8 | Number of decimals. |

### getPool

```solidity
function getPool() public view returns (struct IRigoblockV3PoolState.ReturnedPool)
```

Returns the struct containing pool initialization parameters.

_Symbol is stored as bytes8 but returned as string in the returned struct, unlocked is omitted as alwasy true._

#### Return Values

| Name | Type                                      | Description          |
| ---- | ----------------------------------------- | -------------------- |
| \[0] | struct IRigoblockV3PoolState.ReturnedPool | ReturnedPool struct. |

### getPoolParams

```solidity
function getPoolParams() public view returns (struct IRigoblockV3PoolState.PoolParams)
```

Returns the struct compaining pool parameters.

#### Return Values

| Name | Type                                    | Description        |
| ---- | --------------------------------------- | ------------------ |
| \[0] | struct IRigoblockV3PoolState.PoolParams | PoolParams struct. |

### getPoolTokens

```solidity
function getPoolTokens() public view returns (struct IRigoblockV3PoolState.PoolTokens)
```

Returns the struct containing pool tokens info.

#### Return Values

| Name | Type                                    | Description        |
| ---- | --------------------------------------- | ------------------ |
| \[0] | struct IRigoblockV3PoolState.PoolTokens | PoolTokens struct. |

### name

```solidity
function name() public view returns (string)
```

Returns a string of the pool name.

_Name maximum length 31 bytes._

#### Return Values

| Name | Type   | Description         |
| ---- | ------ | ------------------- |
| \[0] | string | String of the name. |

### symbol

```solidity
function symbol() public view returns (string)
```

Returns a string of the pool symbol.

#### Return Values

| Name | Type   | Description           |
| ---- | ------ | --------------------- |
| \[0] | string | String of the symbol. |

### totalSupply

```solidity
function totalSupply() public view returns (uint256)
```

### \_getFeeCollector

```solidity
function _getFeeCollector() internal view returns (address)
```

### \_getMinPeriod

```solidity
function _getMinPeriod() internal view returns (uint48)
```

### \_getSpread

```solidity
function _getSpread() internal view returns (uint16)
```

### \_getUnitaryValue

```solidity
function _getUnitaryValue() internal view returns (uint256)
```
