# ISmartPoolState

## Overview

#### License: Apache 2.0-or-later

```solidity
interface ISmartPoolState
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Structs info

### ActiveTokens

```solidity
struct ActiveTokens {
	address[] activeTokens;
	address baseToken;
}
```


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

### getAcceptedMintTokens (0xd0624bed)

```solidity
function getAcceptedMintTokens()
    external
    view
    returns (address[] memory tokens)
```

Returns the list of accepted mint tokens.


Return values:

| Name   | Type      | Description               |
| :----- | :-------- | :------------------------ |
| tokens | address[] | Array of token addresses. |

### getActiveApplications (0x935ef3ad)

```solidity
function getActiveApplications()
    external
    view
    returns (uint256 packedApplications)
```

Returns the active application flags.


Return values:

| Name               | Type    | Description                                  |
| :----------------- | :------ | :------------------------------------------- |
| packedApplications | uint256 | Packed value of bitmap encoded active flags. |

### getActiveTokens (0x5f5817e3)

```solidity
function getActiveTokens()
    external
    view
    returns (ISmartPoolState.ActiveTokens memory tokens)
```

Returns the list of active tokens and the base token.

Base token is always active.

Return values:

| Name   | Type                                | Description                                  |
| :----- | :---------------------------------- | :------------------------------------------- |
| tokens | struct ISmartPoolState.ActiveTokens | Tuple of active tokens list and base token.  |

### getPool (0x026b1d5f)

```solidity
function getPool() external view returns (ISmartPoolState.ReturnedPool memory)
```

Returns the struct containing pool initialization parameters.

Symbol is stored as bytes8 but returned as string in the returned struct, unlocked is omitted as alwasy true.


Return values:

| Name | Type                                | Description          |
| :--- | :---------------------------------- | :------------------- |
| [0]  | struct ISmartPoolState.ReturnedPool | ReturnedPool struct. |

### getPoolParams (0x42377107)

```solidity
function getPoolParams()
    external
    view
    returns (ISmartPoolState.PoolParams memory)
```

Returns the struct compaining pool parameters.


Return values:

| Name | Type                              | Description        |
| :--- | :-------------------------------- | :----------------- |
| [0]  | struct ISmartPoolState.PoolParams | PoolParams struct. |

### getPoolTokens (0x89c06568)

```solidity
function getPoolTokens()
    external
    view
    returns (ISmartPoolState.PoolTokens memory)
```

Returns the struct containing pool tokens info.


Return values:

| Name | Type                              | Description         |
| :--- | :-------------------------------- | :------------------ |
| [0]  | struct ISmartPoolState.PoolTokens | PoolTokens struct.  |

### getPoolStorage (0x95f71b16)

```solidity
function getPoolStorage()
    external
    view
    returns (
        ISmartPoolState.ReturnedPool memory poolInitParams,
        ISmartPoolState.PoolParams memory poolVariables,
        ISmartPoolState.PoolTokens memory poolTokensInfo
    )
```

Returns the aggregate pool generic storage.


Return values:

| Name           | Type                                | Description                            |
| :------------- | :---------------------------------- | :------------------------------------- |
| poolInitParams | struct ISmartPoolState.ReturnedPool | The pool's initialization parameters.  |
| poolVariables  | struct ISmartPoolState.PoolParams   | The pool's variables.                  |
| poolTokensInfo | struct ISmartPoolState.PoolTokens   | The pool's tokens info.                |

### getUserAccount (0xfb47e016)

```solidity
function getUserAccount(
    address _who
) external view returns (ISmartPoolState.UserAccount memory)
```

Returns a pool holder's account struct.


Return values:

| Name | Type                               | Description         |
| :--- | :--------------------------------- | :------------------ |
| [0]  | struct ISmartPoolState.UserAccount | UserAccount struct. |

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

### balanceOf (0x70a08231)

```solidity
function balanceOf(address who) external view returns (uint256)
```

Returns the balance of pool tokens for a given holder.


Parameters:

| Name | Type    | Description                   |
| :--- | :------ | :---------------------------- |
| who  | address | Address of the token holder.  |


Return values:

| Name | Type    | Description                 |
| :--- | :------ | :-------------------------- |
| [0]  | uint256 | Number of pool tokens held. |

### decimals (0x313ce567)

```solidity
function decimals() external view returns (uint8)
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
) external view returns (bool approved)
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

### getDelegatedAddresses (0xe598a475)

```solidity
function getDelegatedAddresses(
    bytes4 selector
) external view returns (address[] memory addresses)
```

Returns all addresses currently granted delegated write access to a selector.


Parameters:

| Name     | Type   | Description                              |
| :------- | :----- | :--------------------------------------- |
| selector | bytes4 | The adapter function selector to query.  |


Return values:

| Name      | Type      | Description                                                 |
| :-------- | :-------- | :---------------------------------------------------------- |
| addresses | address[] | Array of addresses with delegated access for that selector. |

### getDelegatedSelectors (0xe496fb4a)

```solidity
function getDelegatedSelectors(
    address delegated
) external view returns (bytes4[] memory selectors)
```

Returns all selectors currently delegated to an address.


Parameters:

| Name      | Type    | Description            |
| :-------- | :------ | :--------------------- |
| delegated | address | The address to query.  |


Return values:

| Name      | Type     | Description                                                |
| :-------- | :------- | :--------------------------------------------------------- |
| selectors | bytes4[] | Array of selectors the address has been granted access to. |
