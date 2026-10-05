# LibCobbDouglas

## Overview

#### License: Apache 2.0

```solidity
library LibCobbDouglas
```


## Functions info

### cobbDouglas

```solidity
function cobbDouglas(
    uint256 totalRewards,
    uint256 fees,
    uint256 totalFees,
    uint256 stake,
    uint256 totalStake,
    uint32 alphaNumerator,
    uint32 alphaDenominator
) internal pure returns (uint256 rewards)
```

The cobb-douglas function used to compute fee-based rewards for
staking pools in a given epoch. This function does not perform
bounds checking on the inputs, but the following conditions
need to be true:
0 <= fees / totalFees <= 1
0 <= stake / totalStake <= 1
0 <= alphaNumerator / alphaDenominator <= 1


Parameters:

| Name             | Type    | Description                                                 |
| :--------------- | :------ | :---------------------------------------------------------- |
| totalRewards     | uint256 | collected over an epoch.                                    |
| fees             | uint256 | Fees attributed to the the staking pool.                    |
| totalFees        | uint256 | Total fees collected across all pools that earned rewards.  |
| stake            | uint256 | Stake attributed to the staking pool.                       |
| totalStake       | uint256 | Total stake across all pools that earned rewards.           |
| alphaNumerator   | uint32  | Numerator of `alpha` in the cobb-douglas function.          |
| alphaDenominator | uint32  | Denominator of `alpha` in the cobb-douglas function.        |


Return values:

| Name    | Type    | Description                       |
| :------ | :------ | :-------------------------------- |
| rewards | uint256 | Rewards owed to the staking pool. |
