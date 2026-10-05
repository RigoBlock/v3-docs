# IOwnable

## Overview

#### License: Apache 2.0

```solidity
abstract contract IOwnable
```


## Events info

### OwnershipTransferred

```solidity
event OwnershipTransferred(address indexed previousOwner, address indexed newOwner)
```

Emitted by Ownable when ownership is transferred.


Parameters:

| Name          | Type    | Description                          |
| :------------ | :------ | :----------------------------------- |
| previousOwner | address | The previous owner of the contract.  |
| newOwner      | address | The new owner of the contract.       |

## Functions info

### transferOwnership (0xf2fde38b)

```solidity
function transferOwnership(address newOwner) public virtual
```

Transfers ownership of the contract to a new address.


Parameters:

| Name     | Type    | Description                             |
| :------- | :------ | :-------------------------------------- |
| newOwner | address | The address that will become the owner. |
