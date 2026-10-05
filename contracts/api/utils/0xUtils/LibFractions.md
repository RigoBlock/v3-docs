# LibFractions

## Overview

#### License: Apache 2.0

```solidity
library LibFractions
```


## Functions info

### add

```solidity
function add(
    uint256 n1,
    uint256 d1,
    uint256 n2,
    uint256 d2
) internal pure returns (uint256 numerator, uint256 denominator)
```

Safely adds two fractions `n1/d1 + n2/d2`


Parameters:

| Name | Type    | Description         |
| :--- | :------ | :------------------ |
| n1   | uint256 | numerator of `1`    |
| d1   | uint256 | denominator of `1`  |
| n2   | uint256 | numerator of `2`    |
| d2   | uint256 | denominator of `2`  |


Return values:

| Name        | Type    | Description        |
| :---------- | :------ | :----------------- |
| numerator   | uint256 | Numerator of sum   |
| denominator | uint256 | Denominator of sum |

### normalize

```solidity
function normalize(
    uint256 numerator,
    uint256 denominator,
    uint256 maxValue
) internal pure returns (uint256 scaledNumerator, uint256 scaledDenominator)
```

Rescales a fraction to prevent overflows during addition if either
the numerator or the denominator are > `maxValue`.


Parameters:

| Name        | Type    | Description                                                        |
| :---------- | :------ | :----------------------------------------------------------------- |
| numerator   | uint256 | The numerator.                                                     |
| denominator | uint256 | The denominator.                                                   |
| maxValue    | uint256 | The maximum value allowed for both the numerator and denominator.  |


Return values:

| Name              | Type    | Description               |
| :---------------- | :------ | :------------------------ |
| scaledNumerator   | uint256 | The rescaled numerator.   |
| scaledDenominator | uint256 | The rescaled denominator. |

### normalize

```solidity
function normalize(
    uint256 numerator,
    uint256 denominator
) internal pure returns (uint256 scaledNumerator, uint256 scaledDenominator)
```

Rescales a fraction to prevent overflows during addition if either
the numerator or the denominator are > 2 ** 127.


Parameters:

| Name        | Type    | Description       |
| :---------- | :------ | :---------------- |
| numerator   | uint256 | The numerator.    |
| denominator | uint256 | The denominator.  |


Return values:

| Name              | Type    | Description               |
| :---------------- | :------ | :------------------------ |
| scaledNumerator   | uint256 | The rescaled numerator.   |
| scaledDenominator | uint256 | The rescaled denominator. |

### scaleDifference

```solidity
function scaleDifference(
    uint256 n1,
    uint256 d1,
    uint256 n2,
    uint256 d2,
    uint256 s
) internal pure returns (uint256 result)
```

Safely scales the difference between two fractions.


Parameters:

| Name | Type    | Description                        |
| :--- | :------ | :--------------------------------- |
| n1   | uint256 | numerator of `1`                   |
| d1   | uint256 | denominator of `1`                 |
| n2   | uint256 | numerator of `2`                   |
| d2   | uint256 | denominator of `2`                 |
| s    | uint256 | scalar to multiply by difference.  |


Return values:

| Name   | Type    | Description            |
| :----- | :------ | :--------------------- |
| result | uint256 | `s * (n1/d1 - n2/d2)`. |
