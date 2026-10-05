# LibMath

## Overview

#### License: Apache 2.0

```solidity
library LibMath
```


## Functions info

### safeGetPartialAmountFloor

```solidity
function safeGetPartialAmountFloor(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (uint256 partialAmount)
```

Calculates partial value given a numerator and denominator rounded down.
Reverts if rounding error is >= 0.1%


Parameters:

| Name        | Type    | Description                     |
| :---------- | :------ | :------------------------------ |
| numerator   | uint256 | Numerator.                      |
| denominator | uint256 | Denominator.                    |
| target      | uint256 | Value to calculate partial of.  |


Return values:

| Name          | Type    | Description                           |
| :------------ | :------ | :------------------------------------ |
| partialAmount | uint256 | Partial value of target rounded down. |

### safeGetPartialAmountCeil

```solidity
function safeGetPartialAmountCeil(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (uint256 partialAmount)
```

Calculates partial value given a numerator and denominator rounded down.
Reverts if rounding error is >= 0.1%


Parameters:

| Name        | Type    | Description                     |
| :---------- | :------ | :------------------------------ |
| numerator   | uint256 | Numerator.                      |
| denominator | uint256 | Denominator.                    |
| target      | uint256 | Value to calculate partial of.  |


Return values:

| Name          | Type    | Description                         |
| :------------ | :------ | :---------------------------------- |
| partialAmount | uint256 | Partial value of target rounded up. |

### getPartialAmountFloor

```solidity
function getPartialAmountFloor(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (uint256 partialAmount)
```

Calculates partial value given a numerator and denominator rounded down.


Parameters:

| Name        | Type    | Description                     |
| :---------- | :------ | :------------------------------ |
| numerator   | uint256 | Numerator.                      |
| denominator | uint256 | Denominator.                    |
| target      | uint256 | Value to calculate partial of.  |


Return values:

| Name          | Type    | Description                           |
| :------------ | :------ | :------------------------------------ |
| partialAmount | uint256 | Partial value of target rounded down. |

### getPartialAmountCeil

```solidity
function getPartialAmountCeil(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (uint256 partialAmount)
```

Calculates partial value given a numerator and denominator rounded down.


Parameters:

| Name        | Type    | Description                     |
| :---------- | :------ | :------------------------------ |
| numerator   | uint256 | Numerator.                      |
| denominator | uint256 | Denominator.                    |
| target      | uint256 | Value to calculate partial of.  |


Return values:

| Name          | Type    | Description                         |
| :------------ | :------ | :---------------------------------- |
| partialAmount | uint256 | Partial value of target rounded up. |

### isRoundingErrorFloor

```solidity
function isRoundingErrorFloor(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (bool isError)
```

Checks if rounding error >= 0.1% when rounding down.


Parameters:

| Name        | Type    | Description                                    |
| :---------- | :------ | :--------------------------------------------- |
| numerator   | uint256 | Numerator.                                     |
| denominator | uint256 | Denominator.                                   |
| target      | uint256 | Value to multiply with numerator/denominator.  |


Return values:

| Name    | Type | Description                |
| :------ | :--- | :------------------------- |
| isError | bool | Rounding error is present. |

### isRoundingErrorCeil

```solidity
function isRoundingErrorCeil(
    uint256 numerator,
    uint256 denominator,
    uint256 target
) internal pure returns (bool isError)
```

Checks if rounding error >= 0.1% when rounding up.


Parameters:

| Name        | Type    | Description                                    |
| :---------- | :------ | :--------------------------------------------- |
| numerator   | uint256 | Numerator.                                     |
| denominator | uint256 | Denominator.                                   |
| target      | uint256 | Value to multiply with numerator/denominator.  |


Return values:

| Name    | Type | Description                |
| :------ | :--- | :------------------------- |
| isError | bool | Rounding error is present. |
