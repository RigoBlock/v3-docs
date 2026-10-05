# IAuthorizable

## Overview

#### License: Apache 2.0

```solidity
abstract contract IAuthorizable
```


## Events info

### AuthorizedAddressAdded

```solidity
event AuthorizedAddressAdded(address indexed target, address indexed caller)
```

Emitted when a new address is authorized.


Parameters:

| Name   | Type    | Description                                        |
| :----- | :------ | :------------------------------------------------- |
| target | address | Address of the authorized address.                 |
| caller | address | Address of the address that authorized the target. |

### AuthorizedAddressRemoved

```solidity
event AuthorizedAddressRemoved(address indexed target, address indexed caller)
```

Emitted when a currently authorized address is unauthorized.


Parameters:

| Name   | Type    | Description                                        |
| :----- | :------ | :------------------------------------------------- |
| target | address | Address of the authorized address.                 |
| caller | address | Address of the address that authorized the target. |

## Functions info

### addAuthorizedAddress (0x42f1181e)

```solidity
function addAuthorizedAddress(address target) external virtual
```

Authorizes an address.


Parameters:

| Name   | Type    | Description           |
| :----- | :------ | :-------------------- |
| target | address | Address to authorize. |

### removeAuthorizedAddress (0x70712939)

```solidity
function removeAuthorizedAddress(address target) external virtual
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
) external virtual
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
    virtual
    returns (address[] memory)
```

Gets all authorized addresses.


Return values:

| Name | Type      | Description                    |
| :--- | :-------- | :----------------------------- |
| [0]  | address[] | Array of authorized addresses. |
