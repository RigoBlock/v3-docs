# Ownable

## Overview

#### License: Apache 2.0

```solidity
abstract contract Ownable is IOwnable
```


## State variables info

### owner (0x8da5cb5b)

```solidity
address owner
```

The owner of this contract.


Return values:

| Name | Type | Description |
| :--- | :--- | :---------- |


## Modifiers info

### onlyOwner

```solidity
modifier onlyOwner()
```


## Functions info

### transferOwnership (0xf2fde38b)

```solidity
function transferOwnership(address newOwner) public override onlyOwner
```

Change the owner of this contract.


Parameters:

| Name     | Type    | Description        |
| :------- | :------ | :----------------- |
| newOwner | address | New owner address. |
