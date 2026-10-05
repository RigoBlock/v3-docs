# LibFixedMath

## Overview

#### License: Apache 2.0

```solidity
library LibFixedMath
```

Signed, fixed-point, 127-bit precision math library.
## Functions info

### mul

```solidity
function mul(int256 a, int256 b) internal pure returns (int256 c)
```

Returns the multiplication of two fixed point numbers, reverting on overflow.
### div

```solidity
function div(int256 a, int256 b) internal pure returns (int256 c)
```

Returns the division of two fixed point numbers.
### mulDiv

```solidity
function mulDiv(int256 a, int256 n, int256 d) internal pure returns (int256 c)
```

Performs (a * n) / d, without scaling for precision.
### uintMul

```solidity
function uintMul(int256 f, uint256 u) internal pure returns (uint256)
```

Returns the unsigned integer result of multiplying a fixed-point
number with an integer, reverting if the multiplication overflows.
Negative results are clamped to zero.
### toFixed

```solidity
function toFixed(uint256 n, uint256 d) internal pure returns (int256 f)
```

Convert unsigned `n` / `d` to a fixed-point number.
Reverts if `n` / `d` is too large to fit in a fixed-point number.
### ln

```solidity
function ln(int256 x) internal pure returns (int256 r)
```

Get the natural logarithm of a fixed-point number 0 < `x` <= LN_MAX_VAL
### exp

```solidity
function exp(int256 x) internal pure returns (int256 r)
```

Compute the natural exponent for a fixed-point number EXP_MIN_VAL <= `x` <= 1