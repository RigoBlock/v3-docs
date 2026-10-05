# RigoblockPoolProxyFactory

## Overview

#### License: Apache-2.0-or-later

```solidity
contract RigoblockPoolProxyFactory is IRigoblockPoolProxyFactory
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## State variables info

### implementation (0x5c60da1b)

```solidity
address implementation
```


## Modifiers info

### onlyRigoblockDao

```solidity
modifier onlyRigoblockDao()
```


## Functions info

### constructor

```solidity
constructor(address newImplementation, address registry)
```


### createPool (0x1d7d13cc)

```solidity
function createPool(
    string calldata name,
    string calldata symbol,
    address baseToken
) external override returns (address newPoolAddress, bytes32 poolId)
```

Creates a new Rigoblock pool.


Parameters:

| Name      | Type    | Description                 |
| :-------- | :------ | :-------------------------- |
| name      | string  | String of the name.         |
| symbol    | string  | String of the symbol.       |
| baseToken | address | Address of the base token.  |


Return values:

| Name           | Type    | Description               |
| :------------- | :------ | :------------------------ |
| newPoolAddress | address | Address of the new pool.  |
| poolId         | bytes32 | Id of the new pool.       |

### setImplementation (0xd784d426)

```solidity
function setImplementation(
    address newImplementation
) external override onlyRigoblockDao
```

Allows Rigoblock Dao to update factory pool implementation.


Parameters:

| Name              | Type    | Description                                 |
| :---------------- | :------ | :------------------------------------------ |
| newImplementation | address | Address of the new implementation contract. |

### setRegistry (0xa91ee0dc)

```solidity
function setRegistry(address newRegistry) external override onlyRigoblockDao
```

Allows owner to update the registry.


Parameters:

| Name        | Type    | Description                  |
| :---------- | :------ | :--------------------------- |
| newRegistry | address | Address of the new registry. |

### parameters (0x89035730)

```solidity
function parameters()
    external
    view
    override
    returns (IRigoblockPoolProxyFactory.Parameters memory)
```

Returns the pool initialization parameters at proxy deploy.


Return values:

| Name | Type                                         | Description                   |
| :--- | :------------------------------------------- | :---------------------------- |
| [0]  | struct IRigoblockPoolProxyFactory.Parameters | Tuple of the pool parameters. |

### getRegistry (0x5ab1bd53)

```solidity
function getRegistry() public view override returns (address)
```

Returns the address of the pool registry.


Return values:

| Name | Type    | Description              |
| :--- | :------ | :----------------------- |
| [0]  | address | Address of the registry. |
