# IAuthority

## Overview

#### License: Apache 2.0

```solidity
interface IAuthority
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Enums info

### Role

```solidity
enum Role {
	 ADAPTER,
	 FACTORY,
	 WHITELISTER
}
```


## Structs info

### Permission

```solidity
struct Permission {
	mapping(IAuthority.Role => bool) authorized;
}
```

Mapping of permission type to bool.


Parameters:

| Name | Description |
| :--- | :---------- |



Return values:

| Name | Type | Description |
| :--- | :--- | :---------- |


## Events info

### PermissionAdded

```solidity
event PermissionAdded(address indexed from, address indexed target, uint8 indexed permissionType)
```

Adds a permission for a role.

Possible roles are Role.ADAPTER, Role.FACTORY, Role.WHITELISTER


Parameters:

| Name           | Type    | Description                      |
| :------------- | :------ | :------------------------------- |
| from           | address | Address of the method caller.    |
| target         | address | Address of the approved wallet.  |
| permissionType | uint8   | Enum type of permission.         |

### PermissionRemoved

```solidity
event PermissionRemoved(address indexed from, address indexed target, uint8 indexed permissionType)
```

Removes a permission for a role.

Possible roles are Role.ADAPTER, Role.FACTORY, Role.WHITELISTER


Parameters:

| Name           | Type    | Description                      |
| :------------- | :------ | :------------------------------- |
| from           | address | Address of the  method caller.   |
| target         | address | Address of the approved wallet.  |
| permissionType | uint8   | Enum type of permission.         |

### RemovedMethod

```solidity
event RemovedMethod(address indexed from, address indexed adapter, bytes4 indexed selector)
```

Removes an approved method.

Removes a mapping of method selector to adapter according to eip1967.


Parameters:

| Name     | Type    | Description                     |
| :------- | :------ | :------------------------------ |
| from     | address | Address of the  method caller.  |
| adapter  | address | Address of the adapter.         |
| selector | bytes4  | Bytes4 of the method signature. |

### WhitelistedMethod

```solidity
event WhitelistedMethod(address indexed from, address indexed adapter, bytes4 indexed selector)
```

Approves a new method.

Adds a mapping of method selector to adapter according to eip1967.


Parameters:

| Name     | Type    | Description                     |
| :------- | :------ | :------------------------------ |
| from     | address | Address of the  method caller.  |
| adapter  | address | Address of the adapter.         |
| selector | bytes4  | Bytes4 of the method signature. |

## Functions info

### addMethod (0xcd29d473)

```solidity
function addMethod(bytes4 selector, address adapter) external
```

Allows a whitelister to whitelist a method.


Parameters:

| Name     | Type    | Description                                      |
| :------- | :------ | :----------------------------------------------- |
| selector | bytes4  | Bytes4 hex of the method selector.               |
| adapter  | address | Address of the adapter implementing the method.  |

### removeMethod (0xd9efcc1e)

```solidity
function removeMethod(bytes4 selector, address adapter) external
```

Allows a whitelister to remove a method.


Parameters:

| Name     | Type    | Description                                     |
| :------- | :------ | :---------------------------------------------- |
| selector | bytes4  | Bytes4 hex of the method selector.              |
| adapter  | address | Address of the adapter implementing the method. |

### setAdapter (0x332f6465)

```solidity
function setAdapter(address adapter, bool isWhitelisted) external
```

Allows owner to set extension adapter address.


Parameters:

| Name          | Type    | Description                     |
| :------------ | :------ | :------------------------------ |
| adapter       | address | Address of the target adapter.  |
| isWhitelisted | bool    | Bool whitelisted.               |

### setFactory (0x71013c10)

```solidity
function setFactory(address factory, bool isWhitelisted) external
```

Allows an admin to set factory permission.


Parameters:

| Name          | Type    | Description                     |
| :------------ | :------ | :------------------------------ |
| factory       | address | Address of the target factory.  |
| isWhitelisted | bool    | Bool whitelisted.               |

### setWhitelister (0xc91b0149)

```solidity
function setWhitelister(address whitelister, bool isWhitelisted) external
```

Allows the owner to set whitelister permission.


Parameters:

| Name          | Type    | Description                  |
| :------------ | :------ | :--------------------------- |
| whitelister   | address | Address of the whitelister.  |
| isWhitelisted | bool    | Bool whitelisted.            |

### getApplicationAdapter (0xc348fa19)

```solidity
function getApplicationAdapter(bytes4 selector) external view returns (address)
```

Returns the address of the adapter associated to the signature.


Parameters:

| Name     | Type   | Description                   |
| :------- | :----- | :---------------------------- |
| selector | bytes4 | Hex of the method signature.  |


Return values:

| Name | Type    | Description             |
| :--- | :------ | :---------------------- |
| [0]  | address | Address of the adapter. |

### isWhitelistedFactory (0xdcb7a3e0)

```solidity
function isWhitelistedFactory(address target) external view returns (bool)
```

Provides whether a factory is whitelisted.


Parameters:

| Name   | Type    | Description                     |
| :----- | :------ | :------------------------------ |
| target | address | Address of the target factory.  |


Return values:

| Name | Type | Description          |
| :--- | :--- | :------------------- |
| [0]  | bool | Bool is whitelisted. |

### isWhitelister (0x7d0c269f)

```solidity
function isWhitelister(address target) external view returns (bool)
```

Provides whether an address is whitelister.


Parameters:

| Name   | Type    | Description                         |
| :----- | :------ | :---------------------------------- |
| target | address | Address of the target whitelister.  |


Return values:

| Name | Type | Description          |
| :--- | :--- | :------------------- |
| [0]  | bool | Bool is whitelisted. |
