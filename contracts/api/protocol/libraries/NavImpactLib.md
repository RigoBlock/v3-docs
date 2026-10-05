# NavImpactLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library NavImpactLib
```

Author: Gabriele Rigo - <gab@rigoblock.com>
Provides percentage-based NAV impact validation for cross-chain transfers

Used by both AIntents (source) and ECrosschain (destination) for consistent validation

## Errors info

### EffectiveSupplyTooLow

```solidity
error EffectiveSupplyTooLow()
```


### NavImpactTooHigh

```solidity
error NavImpactTooHigh()
```

Thrown when transfer amount exceeds maximum allowed NAV impact

Impact is calculated as (transferValue * 10000) / totalAssetsValue in basis points
## Functions info

### validateNavImpact

```solidity
function validateNavImpact(
    address token,
    uint256 amount,
    uint256 toleranceBps
) internal view
```

Validates that transfer amount doesn't exceed NAV impact tolerance

Calculates percentage impact: (transferValue * 10000) / totalAssetsValue vs toleranceBps


Parameters:

| Name         | Type    | Description                                                   |
| :----------- | :------ | :------------------------------------------------------------ |
| token        | address | Token being transferred                                       |
| amount       | uint256 | Amount being transferred                                      |
| toleranceBps | uint256 | Maximum allowed NAV impact in basis points (e.g., 1000 = 10%) |

### validateSupply

```solidity
function validateSupply(
    uint256 totalSupply,
    int256 virtualSupply
) internal pure
```

Validates that effective supply meets minimum threshold when virtual supply is negative