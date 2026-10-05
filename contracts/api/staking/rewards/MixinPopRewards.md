# MixinPopRewards

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinPopRewards is MixinPopManager, MixinStakingPool, MixinFinalizer
```


## Modifiers info

### onlyPop

```solidity
modifier onlyPop()
```

Asserts that the call is coming from a valid pop.
## Functions info

### creditPopReward (0xecc128f2)

```solidity
function creditPopReward(
    address poolAccount,
    uint256 popReward
) external payable override onlyPop
```

Credits the value of a pool's pop reward.

Only a known RigoBlock pop can call this method. See (MixinPopManager).


Parameters:

| Name        | Type    | Description                                 |
| :---------- | :------ | :------------------------------------------ |
| poolAccount | address | The address of the rigoblock pool account.  |
| popReward   | uint256 | The pop reward.                             |

### getStakingPoolStatsThisEpoch (0x46b97959)

```solidity
function getStakingPoolStatsThisEpoch(
    bytes32 poolId
) external view override returns (IStructs.PoolStats memory)
```

Get stats on a staking pool in this epoch.


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| poolId | bytes32 | Pool Id to query.  |


Return values:

| Name | Type                      | Description                   |
| :--- | :------------------------ | :---------------------------- |
| [0]  | struct IStructs.PoolStats | PoolStats struct for pool id. |
