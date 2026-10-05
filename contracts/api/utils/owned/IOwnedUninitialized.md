# IOwnedUninitialized

## Overview

#### License: Apache 2.0

```solidity
interface IOwnedUninitialized
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Events info

### NewOwner

```solidity
event NewOwner(address indexed old, address indexed current)
```

Emitted when new owner is set.


Parameters:

| Name    | Type    | Description                     |
| :------ | :------ | :------------------------------ |
| old     | address | Address of the previous owner.  |
| current | address | Address of the new owner.       |

## Functions info

### setOwner (0x13af4035)

```solidity
function setOwner(address newOwner) external
```

Allows current owner to set a new owner address.

Method restricted to owner.


Parameters:

| Name     | Type    | Description               |
| :------- | :------ | :------------------------ |
| newOwner | address | Address of the new owner. |

### owner (0x8da5cb5b)

```solidity
function owner() external view returns (address)
```

Returns the address of the owner.


Return values:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| [0]  | address | Address of the owner. |
