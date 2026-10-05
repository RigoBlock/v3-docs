# PoolRegistry

## Overview

#### License: Apache 2.0

```solidity
contract PoolRegistry is IPoolRegistry
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## State variables info

### authority (0xbf7e214f)

```solidity
address authority
```


### rigoblockDao (0x3edd80c3)

```solidity
address rigoblockDao
```


## Modifiers info

### onlyWhitelistedFactory

```solidity
modifier onlyWhitelistedFactory()
```


### onlyPoolOperator

```solidity
modifier onlyPoolOperator(address pool)
```


### onlyRigoblockDao

```solidity
modifier onlyRigoblockDao()
```


### whenAddressFree

```solidity
modifier whenAddressFree(address pool)
```


### whenPoolRegistered

```solidity
modifier whenPoolRegistered(address pool)
```


## Functions info

### constructor

```solidity
constructor(address newAuthority, address newRigoblockDao)
```


### register (0x3f47734b)

```solidity
function register(
    address pool,
    string calldata name,
    string calldata symbol,
    bytes32 poolId
) external override onlyWhitelistedFactory whenAddressFree(pool)
```

Allows a factory which is an authority to register a pool.


Parameters:

| Name   | Type    | Description                                             |
| :----- | :------ | :------------------------------------------------------ |
| pool   | address | Address of the pool.                                    |
| name   | string  | String name of the pool (31 characters/bytes or less).  |
| symbol | string  | String symbol of the pool (3 to 5 characters/bytes).    |
| poolId | bytes32 | Bytes32 of the pool id.                                 |

### setAuthority (0x7a9e5e4b)

```solidity
function setAuthority(address newAuthority) external override onlyRigoblockDao
```

Allows Rigoblock governance to update authority.


Parameters:

| Name      | Type    | Description                        |
| :-------- | :------ | :--------------------------------- |
| authority | address | Address of the authority contract. |

### setMeta (0x56d002c4)

```solidity
function setMeta(
    address pool,
    bytes32 key,
    bytes32 value
) external override onlyPoolOperator(pool) whenPoolRegistered(pool)
```

Allows pool owner to set metadata for a pool.


Parameters:

| Name  | Type    | Description           |
| :---- | :------ | :-------------------- |
| pool  | address | Address of the pool.  |
| key   | bytes32 | Bytes32 of the key.   |
| value | bytes32 | Bytes32 of the value. |

### setRigoblockDao (0xb516e6e1)

```solidity
function setRigoblockDao(
    address newRigoblockDao
) external override onlyRigoblockDao
```

Allows Rigoblock Dao to update its address.

Creates internal record.


Parameters:

| Name            | Type    | Description                   |
| :-------------- | :------ | :---------------------------- |
| newRigoblockDao | address | Address of the Rigoblock Dao. |

### getPoolIdFromAddress (0x2cee2191)

```solidity
function getPoolIdFromAddress(
    address pool
) external view override returns (bytes32 poolId)
```

Returns the id of a pool from its address.


Parameters:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| pool | address | Address of the pool.  |


Return values:

| Name   | Type    | Description             |
| :----- | :------ | :---------------------- |
| poolId | bytes32 | bytes32 id of the pool. |

### getMeta (0x386f5adf)

```solidity
function getMeta(
    address pool,
    bytes32 key
) external view override returns (bytes32 poolMeta)
```

Returns metadata for a given pool.


Parameters:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| pool | address | Address of the pool.  |
| key  | bytes32 | Bytes32 key.          |


Return values:

| Name     | Type    | Description  |
| :------- | :------ | :----------- |
| poolMeta | bytes32 | Meta by key. |
