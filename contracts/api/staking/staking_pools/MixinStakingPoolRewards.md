# MixinStakingPoolRewards

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinStakingPoolRewards is IStaking, MixinAbstract, MixinCumulativeRewards
```


## Functions info

### withdrawDelegatorRewards (0xb510879f)

```solidity
function withdrawDelegatorRewards(bytes32 poolId) external override
```

Withdraws the caller's GRG rewards that have accumulated until the last epoch.


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| poolId | bytes32 | Unique id of pool. |

### computeRewardBalanceOfOperator (0xbb7ef7e0)

```solidity
function computeRewardBalanceOfOperator(
    bytes32 poolId
) external view override returns (uint256 reward)
```

Computes the reward balance in GRG of the operator of a pool.


Parameters:

| Name   | Type    | Description         |
| :----- | :------ | :------------------ |
| poolId | bytes32 | Unique id of pool.  |


Return values:

| Name   | Type    | Description     |
| :----- | :------ | :-------------- |
| reward | uint256 | Balance in GRG. |

### computeRewardBalanceOfDelegator (0xe907f003)

```solidity
function computeRewardBalanceOfDelegator(
    bytes32 poolId,
    address member
) external view override returns (uint256 reward)
```

Computes the reward balance in GRG of a specific member of a pool.


Parameters:

| Name   | Type    | Description              |
| :----- | :------ | :----------------------- |
| poolId | bytes32 | Unique id of pool.       |
| member | address | The member of the pool.  |


Return values:

| Name   | Type    | Description     |
| :----- | :------ | :-------------- |
| reward | uint256 | Balance in GRG. |
