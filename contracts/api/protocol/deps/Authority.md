# Authority

## Overview

#### License: Apache 2.0

```solidity
contract Authority is Owned, IAuthority
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Modifiers info

### onlyWhitelister

```solidity
modifier onlyWhitelister()
```


## Functions info

### constructor

```solidity
constructor(address newOwner)
```


### addMethod (0xcd29d473)

```solidity
function addMethod(
    bytes4 selector,
    address adapter
) external override onlyWhitelister
```

Allows a whitelister to whitelist a method.


Parameters:

| Name     | Type    | Description                                      |
| :------- | :------ | :----------------------------------------------- |
| selector | bytes4  | Bytes4 hex of the method selector.               |
| adapter  | address | Address of the adapter implementing the method.  |

### removeMethod (0xd9efcc1e)

```solidity
function removeMethod(
    bytes4 selector,
    address adapter
) external override onlyWhitelister
```

Allows a whitelister to remove a method.


Parameters:

| Name     | Type    | Description                                     |
| :------- | :------ | :---------------------------------------------- |
| selector | bytes4  | Bytes4 hex of the method selector.              |
| adapter  | address | Address of the adapter implementing the method. |

### setWhitelister (0xc91b0149)

```solidity
function setWhitelister(
    address whitelister,
    bool isWhitelisted
) external override onlyOwner
```

Allows the owner to set whitelister permission.


Parameters:

| Name          | Type    | Description                  |
| :------------ | :------ | :--------------------------- |
| whitelister   | address | Address of the whitelister.  |
| isWhitelisted | bool    | Bool whitelisted.            |

### setAdapter (0x332f6465)

```solidity
function setAdapter(
    address adapter,
    bool isWhitelisted
) external override onlyOwner
```

Allows owner to set extension adapter address.


Parameters:

| Name          | Type    | Description                     |
| :------------ | :------ | :------------------------------ |
| adapter       | address | Address of the target adapter.  |
| isWhitelisted | bool    | Bool whitelisted.               |

### setFactory (0x71013c10)

```solidity
function setFactory(
    address factory,
    bool isWhitelisted
) external override onlyOwner
```

Allows an admin to set factory permission.


Parameters:

| Name          | Type    | Description                     |
| :------------ | :------ | :------------------------------ |
| factory       | address | Address of the target factory.  |
| isWhitelisted | bool    | Bool whitelisted.               |

### isWhitelistedFactory (0xdcb7a3e0)

```solidity
function isWhitelistedFactory(
    address target
) external view override returns (bool)
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

### getApplicationAdapter (0xc348fa19)

```solidity
function getApplicationAdapter(
    bytes4 selector
) external view override returns (address)
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

### isWhitelister (0x7d0c269f)

```solidity
function isWhitelister(address target) public view override returns (bool)
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
