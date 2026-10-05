# Authorizable

## Overview

#### License: Apache 2.0

```solidity
abstract contract Authorizable is Ownable, IAuthorizable
```


## State variables info

### authorized (0xb9181611)

```solidity
mapping(address => bool) authorized
```

Whether an address is authorized to call privileged functions.

0 Address to query.


Return values:

| Name | Type | Description |
| :--- | :--- | :---------- |


### authorities (0x494503d4)

```solidity
address[] authorities
```

Whether an adderss is authorized to call privileged functions.

0 Index of authorized address.


Return values:

| Name | Type | Description |
| :--- | :--- | :---------- |


## Modifiers info

### onlyAuthorized

```solidity
modifier onlyAuthorized()
```

Only authorized addresses can invoke functions with this modifier.
## Functions info

### addAuthorizedAddress (0x42f1181e)

```solidity
function addAuthorizedAddress(address target) external override onlyOwner
```

Authorizes an address.


Parameters:

| Name   | Type    | Description           |
| :----- | :------ | :-------------------- |
| target | address | Address to authorize. |

### removeAuthorizedAddress (0x70712939)

```solidity
function removeAuthorizedAddress(address target) external override onlyOwner
```

Removes authorizion of an address.


Parameters:

| Name   | Type    | Description                           |
| :----- | :------ | :------------------------------------ |
| target | address | Address to remove authorization from. |

### removeAuthorizedAddressAtIndex (0x9ad26744)

```solidity
function removeAuthorizedAddressAtIndex(
    address target,
    uint256 index
) external override onlyOwner
```

Removes authorizion of an address.


Parameters:

| Name   | Type    | Description                            |
| :----- | :------ | :------------------------------------- |
| target | address | Address to remove authorization from.  |
| index  | uint256 | Index of target in authorities array.  |

### getAuthorizedAddresses (0xd39de6e9)

```solidity
function getAuthorizedAddresses()
    external
    view
    override
    returns (address[] memory)
```

Gets all authorized addresses.


Return values:

| Name | Type      | Description                    |
| :--- | :-------- | :----------------------------- |
| [0]  | address[] | Array of authorized addresses. |
