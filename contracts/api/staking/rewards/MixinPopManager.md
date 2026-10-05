# MixinPopManager

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinPopManager is IStaking, IStakingEvents, MixinStorage
```


## Functions info

### addPopAddress (0x1f81eb80)

```solidity
function addPopAddress(address addr) external override onlyAuthorized
```

Adds a new proof_of_performance address.


Parameters:

| Name | Type    | Description                                      |
| :--- | :------ | :----------------------------------------------- |
| addr | address | Address of proof_of_performance contract to add. |

### removePopAddress (0x36d7dd8e)

```solidity
function removePopAddress(address addr) external override onlyAuthorized
```

Removes an existing proof_of_performance address.


Parameters:

| Name | Type    | Description                                         |
| :--- | :------ | :-------------------------------------------------- |
| addr | address | Address of proof_of_performance contract to remove. |
