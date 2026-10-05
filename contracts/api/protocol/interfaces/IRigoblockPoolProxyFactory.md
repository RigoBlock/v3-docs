# IRigoblockPoolProxyFactory

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IRigoblockPoolProxyFactory
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Structs info

### Parameters

```solidity
struct Parameters {
	string name;
	bytes8 symbol;
	address owner;
	address baseToken;
}
```

Pool initialization parameters.

params: baseToken Address of the base token.
## Events info

### PoolCreated

```solidity
event PoolCreated(address poolAddress)
```

Emitted when a new pool is created.


Parameters:

| Name        | Type    | Description              |
| :---------- | :------ | :----------------------- |
| poolAddress | address | Address of the new pool. |

### Upgraded

```solidity
event Upgraded(address indexed implementation)
```

Emitted when a new implementation is set by the Rigoblock Dao.


Parameters:

| Name           | Type    | Description                        |
| :------------- | :------ | :--------------------------------- |
| implementation | address | Address of the new implementation. |

### RegistryUpgraded

```solidity
event RegistryUpgraded(address indexed registry)
```

Emitted when registry address is upgraded by the Rigoblock Dao.


Parameters:

| Name     | Type    | Description                  |
| :------- | :------ | :--------------------------- |
| registry | address | Address of the new registry. |

## Functions info

### implementation (0x5c60da1b)

```solidity
function implementation() external view returns (address)
```

Returns the implementation address for the pool proxies.


Return values:

| Name | Type    | Description                    |
| :--- | :------ | :----------------------------- |
| [0]  | address | Address of the implementation. |

### createPool (0x1d7d13cc)

```solidity
function createPool(
    string calldata name,
    string calldata symbol,
    address baseToken
) external returns (address newPoolAddress, bytes32 poolId)
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
function setImplementation(address newImplementation) external
```

Allows Rigoblock Dao to update factory pool implementation.


Parameters:

| Name              | Type    | Description                                 |
| :---------------- | :------ | :------------------------------------------ |
| newImplementation | address | Address of the new implementation contract. |

### setRegistry (0xa91ee0dc)

```solidity
function setRegistry(address newRegistry) external
```

Allows owner to update the registry.


Parameters:

| Name        | Type    | Description                  |
| :---------- | :------ | :--------------------------- |
| newRegistry | address | Address of the new registry. |

### getRegistry (0x5ab1bd53)

```solidity
function getRegistry() external view returns (address)
```

Returns the address of the pool registry.


Return values:

| Name | Type    | Description              |
| :--- | :------ | :----------------------- |
| [0]  | address | Address of the registry. |

### parameters (0x89035730)

```solidity
function parameters()
    external
    view
    returns (IRigoblockPoolProxyFactory.Parameters memory)
```

Returns the pool initialization parameters at proxy deploy.


Return values:

| Name | Type                                         | Description                   |
| :--- | :------------------------------------------- | :---------------------------- |
| [0]  | struct IRigoblockPoolProxyFactory.Parameters | Tuple of the pool parameters. |
