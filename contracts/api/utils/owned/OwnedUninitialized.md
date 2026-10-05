# OwnedUninitialized

## Overview

#### License: Apache 2.0

```solidity
abstract contract OwnedUninitialized is IOwnedUninitialized
```


## State variables info

### owner (0x8da5cb5b)

```solidity
address owner
```


## Modifiers info

### onlyOwner

```solidity
modifier onlyOwner()
```


## Functions info

### setOwner (0x13af4035)

```solidity
function setOwner(address newOwner) public override onlyOwner
```

Allows current owner to set a new owner address.

Method restricted to owner.


Parameters:

| Name     | Type    | Description               |
| :------- | :------ | :------------------------ |
| newOwner | address | Address of the new owner. |
