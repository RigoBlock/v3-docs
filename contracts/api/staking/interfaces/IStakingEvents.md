# IStakingEvents

## Overview

#### License: Apache 2.0

```solidity
interface IStakingEvents
```


## Events info

### Stake

```solidity
event Stake(address indexed staker, uint256 amount)
```

Emitted by MixinStake when GRG is staked.


Parameters:

| Name   | Type    | Description    |
| :----- | :------ | :------------- |
| staker | address | of GRG.        |
| amount | uint256 | of GRG staked. |

### Unstake

```solidity
event Unstake(address indexed staker, uint256 amount)
```

Emitted by MixinStake when GRG is unstaked.


Parameters:

| Name   | Type    | Description      |
| :----- | :------ | :--------------- |
| staker | address | of GRG.          |
| amount | uint256 | of GRG unstaked. |

### MoveStake

```solidity
event MoveStake(address indexed staker, uint256 amount, uint8 fromStatus, bytes32 indexed fromPool, uint8 toStatus, bytes32 indexed toPool)
```

Emitted by MixinStake when GRG is unstaked.


Parameters:

| Name   | Type    | Description      |
| :----- | :------ | :--------------- |
| staker | address | of GRG.          |
| amount | uint256 | of GRG unstaked. |

### PopAdded

```solidity
event PopAdded(address exchangeAddress)
```

Emitted by MixinExchangeManager when an exchange is added.


Parameters:

| Name            | Type    | Description              |
| :-------------- | :------ | :----------------------- |
| exchangeAddress | address | Address of new exchange. |

### PopRemoved

```solidity
event PopRemoved(address exchangeAddress)
```

Emitted by MixinExchangeManager when an exchange is removed.


Parameters:

| Name            | Type    | Description                  |
| :-------------- | :------ | :--------------------------- |
| exchangeAddress | address | Address of removed exchange. |

### StakingPoolEarnedRewardsInEpoch

```solidity
event StakingPoolEarnedRewardsInEpoch(uint256 indexed epoch, bytes32 indexed poolId)
```

Emitted by MixinExchangeFees when a pool starts earning rewards in an epoch.


Parameters:

| Name   | Type    | Description                                  |
| :----- | :------ | :------------------------------------------- |
| epoch  | uint256 | The epoch in which the pool earned rewards.  |
| poolId | bytes32 | The ID of the pool.                          |

### EpochEnded

```solidity
event EpochEnded(uint256 indexed epoch, uint256 numPoolsToFinalize, uint256 rewardsAvailable, uint256 totalFeesCollected, uint256 totalWeightedStake)
```

Emitted by MixinFinalizer when an epoch has ended.


Parameters:

| Name               | Type    | Description                                                                |
| :----------------- | :------ | :------------------------------------------------------------------------- |
| epoch              | uint256 | The epoch that ended.                                                      |
| numPoolsToFinalize | uint256 | Number of pools that earned rewards during `epoch` and must be finalized.  |
| rewardsAvailable   | uint256 | Rewards available to all pools that earned rewards during `epoch`.         |
| totalWeightedStake | uint256 | Total weighted stake across all pools that earned rewards during `epoch`.  |
| totalFeesCollected | uint256 | Total fees collected across all pools that earned rewards during `epoch`.  |

### EpochFinalized

```solidity
event EpochFinalized(uint256 indexed epoch, uint256 rewardsPaid, uint256 rewardsRemaining)
```

Emitted by MixinFinalizer when an epoch is fully finalized.


Parameters:

| Name             | Type    | Description                        |
| :--------------- | :------ | :--------------------------------- |
| epoch            | uint256 | The epoch being finalized.         |
| rewardsPaid      | uint256 | Total amount of rewards paid out.  |
| rewardsRemaining | uint256 | Rewards left over.                 |

### RewardsPaid

```solidity
event RewardsPaid(uint256 indexed epoch, bytes32 indexed poolId, uint256 operatorReward, uint256 membersReward)
```

Emitted by MixinFinalizer when rewards are paid out to a pool.


Parameters:

| Name           | Type    | Description                                |
| :------------- | :------ | :----------------------------------------- |
| epoch          | uint256 | The epoch when the rewards were paid out.  |
| poolId         | bytes32 | The pool's ID.                             |
| operatorReward | uint256 | Amount of reward paid to pool operator.    |
| membersReward  | uint256 | Amount of reward paid to pool members.     |

### ParamsSet

```solidity
event ParamsSet(uint256 epochDurationInSeconds, uint32 rewardDelegatedStakeWeight, uint256 minimumPoolStake, uint256 cobbDouglasAlphaNumerator, uint256 cobbDouglasAlphaDenominator)
```

Emitted whenever staking parameters are changed via the `setParams()` function.


Parameters:

| Name                        | Type    | Description                                                      |
| :-------------------------- | :------ | :--------------------------------------------------------------- |
| epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                  |
| rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm.  |
| minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.   |
| cobbDouglasAlphaNumerator   | uint256 | Numerator for cobb douglas alpha factor.                         |
| cobbDouglasAlphaDenominator | uint256 | Denominator for cobb douglas alpha factor.                       |

### StakingPoolCreated

```solidity
event StakingPoolCreated(bytes32 poolId, address operator, uint32 operatorShare)
```

Emitted by MixinStakingPool when a new pool is created.


Parameters:

| Name          | Type    | Description                                         |
| :------------ | :------ | :-------------------------------------------------- |
| poolId        | bytes32 | Unique id generated for pool.                       |
| operator      | address | The operator (creator) of pool.                     |
| operatorShare | uint32  | The share of rewards given to the operator, in ppm. |

### RbPoolStakingPoolSet

```solidity
event RbPoolStakingPoolSet(address indexed rbPoolAddress, bytes32 indexed poolId)
```

Emitted by MixinStakingPool when a rigoblock pool is added to its staking pool.


Parameters:

| Name          | Type    | Description                     |
| :------------ | :------ | :------------------------------ |
| rbPoolAddress | address | Adress of maker added to pool.  |
| poolId        | bytes32 | Unique id of pool.              |

### OperatorShareDecreased

```solidity
event OperatorShareDecreased(bytes32 indexed poolId, uint32 oldOperatorShare, uint32 newOperatorShare)
```

Emitted when a staking pool's operator share is decreased.


Parameters:

| Name             | Type    | Description                                         |
| :--------------- | :------ | :-------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                  |
| oldOperatorShare | uint32  | Previous share of rewards owned by operator.        |
| newOperatorShare | uint32  | Newly decreased share of rewards owned by operator. |

### GrgMintEvent

```solidity
event GrgMintEvent(uint256 grgAmount)
```

Emitted when an inflation mint call is executed successfully.


Parameters:

| Name      | Type    | Description                                       |
| :-------- | :------ | :------------------------------------------------ |
| grgAmount | uint256 | Amount of GRG tokens minted to the staking proxy. |

### CatchStringEvent

```solidity
event CatchStringEvent(string reason)
```

Emitted whenever an inflation mint call is reverted.


Parameters:

| Name   | Type   | Description                   |
| :----- | :----- | :---------------------------- |
| reason | string | String of the revert message. |

### ReturnDataEvent

```solidity
event ReturnDataEvent(bytes reason)
```

Emitted to catch any other inflation mint call fail.


Parameters:

| Name   | Type  | Description                               |
| :----- | :---- | :---------------------------------------- |
| reason | bytes | Bytes output of the reverted transaction. |
