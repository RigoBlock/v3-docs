# IRigoblockV3PoolState

## Overview

#### License: Apache 2.0

```solidity
interface IRigoblockV3PoolState
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Structs info

### ReturnedPool

```solidity
struct ReturnedPool {
	string name;
	string symbol;
	uint8 decimals;
	address owner;
	address baseToken;
}
```

Returned pool initialization parameters.

Symbol is stored as bytes8 but returned as string to facilitating client view.


Parameters:

| Name      | Type    | Description                                                  |
| :-------- | :------ | :----------------------------------------------------------- |
| name      | string  | String of the pool name (max 32 characters).                 |
| symbol    | string  | String of the pool symbol (from 3 to 5 characters).          |
| decimals  | uint8   | Uint8 decimals.                                              |
| owner     | address | Address of the pool operator.                                |
| baseToken | address | Address of the base token of the pool (0 for base currency). |

### PoolParams

```solidity
struct PoolParams {
	uint48 minPeriod;
	uint16 spread;
	uint16 transactionFee;
	address feeCollector;
	address kycProvider;
}
```

Pool variables.


Parameters:

| Name           | Type    | Description                                               |
| :------------- | :------ | :-------------------------------------------------------- |
| minPeriod      | uint48  | Minimum holding period in seconds.                        |
| spread         | uint16  | Value of spread in basis points (from 0 to +-10%).        |
| transactionFee | uint16  | Value of transaction fee in basis points (from 0 to 1%).  |
| feeCollector   | address | Address of the fee receiver.                              |
| kycProvider    | address | Address of the kyc provider.                              |

### PoolTokens

```solidity
struct PoolTokens {
	uint256 unitaryValue;
	uint256 totalSupply;
}
```

Pool tokens.


Parameters:

| Name         | Type    | Description                             |
| :----------- | :------ | :-------------------------------------- |
| unitaryValue | uint256 | A token's unitary value in base token.  |
| totalSupply  | uint256 | Number of total issued pool tokens.     |

### UserAccount

```solidity
struct UserAccount {
	uint208 userBalance;
	uint48 activation;
}
```

Pool holder account.


Parameters:

| Name        | Type    | Description                     |
| :---------- | :------ | :------------------------------ |
| userBalance | uint208 | Number of tokens held by user.  |
| activation  | uint48  | Time when tokens become active. |

## Functions info

### getPool (0x026b1d5f)

```solidity
function getPool()
    external
    view
    returns (IRigoblockV3PoolState.ReturnedPool memory)
```

Returns the struct containing pool initialization parameters.

Symbol is stored as bytes8 but returned as string in the returned struct, unlocked is omitted as alwasy true.


Return values:

| Name | Type                                      | Description          |
| :--- | :---------------------------------------- | :------------------- |
| [0]  | struct IRigoblockV3PoolState.ReturnedPool | ReturnedPool struct. |

### getPoolParams (0x42377107)

```solidity
function getPoolParams()
    external
    view
    returns (IRigoblockV3PoolState.PoolParams memory)
```

Returns the struct compaining pool parameters.


Return values:

| Name | Type                                    | Description        |
| :--- | :-------------------------------------- | :----------------- |
| [0]  | struct IRigoblockV3PoolState.PoolParams | PoolParams struct. |

### getPoolTokens (0x89c06568)

```solidity
function getPoolTokens()
    external
    view
    returns (IRigoblockV3PoolState.PoolTokens memory)
```

Returns the struct containing pool tokens info.


Return values:

| Name | Type                                    | Description        |
| :--- | :-------------------------------------- | :----------------- |
| [0]  | struct IRigoblockV3PoolState.PoolTokens | PoolTokens struct. |

### getPoolStorage (0x95f71b16)

```solidity
function getPoolStorage()
    external
    view
    returns (
        IRigoblockV3PoolState.ReturnedPool memory poolInitParams,
        IRigoblockV3PoolState.PoolParams memory poolVariables,
        IRigoblockV3PoolState.PoolTokens memory poolTokensInfo
    )
```

Returns the aggregate pool generic storage.


Return values:

| Name           | Type                                      | Description                            |
| :------------- | :---------------------------------------- | :------------------------------------- |
| poolInitParams | struct IRigoblockV3PoolState.ReturnedPool | The pool's initialization parameters.  |
| poolVariables  | struct IRigoblockV3PoolState.PoolParams   | The pool's variables.                  |
| poolTokensInfo | struct IRigoblockV3PoolState.PoolTokens   | The pool's tokens info.                |

### getUserAccount (0xfb47e016)

```solidity
function getUserAccount(
    address _who
) external view returns (IRigoblockV3PoolState.UserAccount memory)
```

Returns a pool holder's account struct.


Return values:

| Name | Type                                     | Description         |
| :--- | :--------------------------------------- | :------------------ |
| [0]  | struct IRigoblockV3PoolState.UserAccount | UserAccount struct. |

### name (0x06fdde03)

```solidity
function name() external view returns (string memory)
```

Returns a string of the pool name.

Name maximum length 31 bytes.


Return values:

| Name | Type   | Description         |
| :--- | :----- | :------------------ |
| [0]  | string | String of the name. |

### owner (0x8da5cb5b)

```solidity
function owner() external view returns (address)
```

Returns the address of the owner.


Return values:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| [0]  | address | Address of the owner. |

### symbol (0x95d89b41)

```solidity
function symbol() external view returns (string memory)
```

Returns a string of the pool symbol.


Return values:

| Name | Type   | Description           |
| :--- | :----- | :-------------------- |
| [0]  | string | String of the symbol. |

### totalSupply (0x18160ddd)

```solidity
function totalSupply() external view returns (uint256)
```

Returns the total amount of issued tokens for this pool.


Return values:

| Name | Type    | Description                    |
| :--- | :------ | :----------------------------- |
| [0]  | uint256 | Number of total issued tokens. |
