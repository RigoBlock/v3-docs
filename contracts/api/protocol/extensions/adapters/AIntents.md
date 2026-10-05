# AIntents

## Overview

#### License: Apache-2.0-or-later

```solidity
contract AIntents is IAIntents, IMinimumVersion, ReentrancyGuardTransient
```

Author: Gabriele Rigo - <gab@rigoblock.com>
This adapter enables Rigoblock smart pools to bridge tokens across chains while maintaining NAV integrity.

Uses synchronized adapter deployment to ensure destination adapters exist before enabling cross-chain features.

## Errors info

### NavToleranceTooHigh

```solidity
error NavToleranceTooHigh()
```


## Modifiers info

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### requiredVersion (0x2ea6c3f0)

```solidity
function requiredVersion() external pure override returns (string memory)
```

Returns the minimum implementation version to use an external application.

Adapters must implement it when modifying proxy state or storage.


Return values:

| Name | Type   | Description                              |
| :--- | :----- | :--------------------------------------- |
| [0]  | string | String of the minimum supported version. |

### constructor

```solidity
constructor(address acrossSpokePoolAddress)
```


### depositV3 (0x770d096f)

```solidity
function depositV3(
    IAIntents.AcrossParams calldata params
) external override nonReentrant onlyDelegateCall
```

Executes a crosschain token transfer to across and updated virtual storage.

Has different method selector than across depositV3 to avoid viaIr compilation.


Parameters:

| Name   | Type                          | Description                     |
| :----- | :---------------------------- | :------------------------------ |
| params | struct IAIntents.AcrossParams | Across params encoded as tuple. |
