# ApplicationsLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library ApplicationsLib
```


## Errors info

### ApplicationIndexBitmaskRange

```solidity
error ApplicationIndexBitmaskRange()
```


## Functions info

### storeApplication

```solidity
function storeApplication(
    ApplicationsSlot storage self,
    uint256 appIndex
) internal
```

Sets an application as active in the bitmask.


Parameters:

| Name     | Type                    | Description                                                 |
| :------- | :---------------------- | :---------------------------------------------------------- |
| self     | struct ApplicationsSlot | The storage slot where the packed applications are stored.  |
| appIndex | uint256                 | The application to set as active.                           |

### removeApplication

```solidity
function removeApplication(
    ApplicationsSlot storage self,
    uint256 appIndex
) internal
```

Removes an application from being active in the bitmask.


Parameters:

| Name     | Type                    | Description                                                 |
| :------- | :---------------------- | :---------------------------------------------------------- |
| self     | struct ApplicationsSlot | The storage slot where the packed applications are stored.  |
| appIndex | uint256                 | The application to remove.                                  |

### isActiveApplication

```solidity
function isActiveApplication(
    uint256 packedApplications,
    uint256 appIndex
) internal pure returns (bool)
```

Checks if an application is active in the bitmask.


Parameters:

| Name               | Type    | Description                                   |
| :----------------- | :------ | :-------------------------------------------- |
| packedApplications | uint256 | The bitmap packed active applications flags.  |
| appIndex           | uint256 | The application to check.                     |


Return values:

| Name | Type | Description                             |
| :--- | :--- | :-------------------------------------- |
| [0]  | bool | bool Whether the application is active. |

### shouldQueryApp

```solidity
function shouldQueryApp(
    uint256 packedApplications,
    uint256 appIndex
) internal pure returns (bool)
```

Returns whether an application should be queried for token balances.

GRG_STAKING is always queried: it is a pre-existing application that self-activates
on the first NAV write, so the active-bit may not be set yet on a fresh pool.


Parameters:

| Name               | Type    | Description                                   |
| :----------------- | :------ | :-------------------------------------------- |
| packedApplications | uint256 | The bitmap packed active applications flags.  |
| appIndex           | uint256 | The application to check.                     |


Return values:

| Name | Type | Description                                     |
| :--- | :--- | :---------------------------------------------- |
| [0]  | bool | bool Whether the application should be queried. |
