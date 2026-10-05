# IStaking

## Overview

#### License: Apache 2.0

```solidity
interface IStaking
```


## Functions info

### addPopAddress (0x1f81eb80)

```solidity
function addPopAddress(address addr) external
```

Adds a new proof_of_performance address.


Parameters:

| Name | Type    | Description                                      |
| :--- | :------ | :----------------------------------------------- |
| addr | address | Address of proof_of_performance contract to add. |

### createStakingPool (0xbe111af4)

```solidity
function createStakingPool(
    address rigoblockPoolAddress
) external returns (bytes32 poolId)
```

Create a new staking pool. The sender will be the staking pal of this pool.

Note that a staking pal must be payable.

When governance updates registry address, pools must be migrated to new registry, or this contract must query from both.


Parameters:

| Name                 | Type    | Description                                                                   |
| :------------------- | :------ | :---------------------------------------------------------------------------- |
| rigoblockPoolAddress | address | Adds rigoblock pool to the created staking pool for convenience if non-null.  |


Return values:

| Name   | Type    | Description                                 |
| :----- | :------ | :------------------------------------------ |
| poolId | bytes32 | The unique pool id generated for this pool. |

### setStakingPalAddress (0x3a832382)

```solidity
function setStakingPalAddress(
    bytes32 poolId,
    address newStakingPalAddress
) external
```

Allows the operator to update the staking pal address.


Parameters:

| Name                 | Type    | Description                     |
| :------------------- | :------ | :------------------------------ |
| poolId               | bytes32 | Unique id of pool.              |
| newStakingPalAddress | address | Address of the new staking pal. |

### decreaseStakingPoolOperatorShare (0x5d91121d)

```solidity
function decreaseStakingPoolOperatorShare(
    bytes32 poolId,
    uint32 newOperatorShare
) external
```

Decreases the operator share for the given pool (i.e. increases pool rewards for members).


Parameters:

| Name             | Type    | Description                                                          |
| :--------------- | :------ | :------------------------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                                   |
| newOperatorShare | uint32  | The newly decreased percentage of any rewards owned by the operator. |

### endEpoch (0x0b9663db)

```solidity
function endEpoch() external returns (uint256 numPoolsToFinalize)
```

Begins a new epoch, preparing the prior one for finalization.

Throws if not enough time has passed between epochs or if the

previous epoch was not fully finalized.


Return values:

| Name               | Type    | Description                      |
| :----------------- | :------ | :------------------------------- |
| numPoolsToFinalize | uint256 | The number of unfinalized pools. |

### finalizePool (0xff691b11)

```solidity
function finalizePool(bytes32 poolId) external
```

Instantly finalizes a single pool that earned rewards in the previous epoch,

crediting it rewards for members and withdrawing operator's rewards as GRG.

This can be called by internal functions that need to finalize a pool immediately.

Does nothing if the pool is already finalized or did not earn rewards in the previous epoch.


Parameters:

| Name   | Type    | Description              |
| :----- | :------ | :----------------------- |
| poolId | bytes32 | The pool ID to finalize. |

### init (0xe1c7392a)

```solidity
function init() external
```

Initialize storage owned by this contract.

This function should not be called directly.

The StakingProxy contract will call it in `attachStakingContract()`.
### moveStake (0x58f6c7e3)

```solidity
function moveStake(
    IStructs.StakeInfo calldata from,
    IStructs.StakeInfo calldata to,
    uint256 amount
) external
```

Moves stake between statuses: 'undelegated' or 'delegated'.

Delegated stake can also be moved between pools.

This change comes into effect next epoch.


Parameters:

| Name   | Type                      | Description                   |
| :----- | :------------------------ | :---------------------------- |
| from   | struct IStructs.StakeInfo | Status to move stake out of.  |
| to     | struct IStructs.StakeInfo | Status to move stake into.    |
| amount | uint256                   | Amount of stake to move.      |

### creditPopReward (0xecc128f2)

```solidity
function creditPopReward(
    address poolAccount,
    uint256 popReward
) external payable
```

Credits the value of a pool's pop reward.

Only a known RigoBlock pop can call this method. See (MixinPopManager).


Parameters:

| Name        | Type    | Description                                 |
| :---------- | :------ | :------------------------------------------ |
| poolAccount | address | The address of the rigoblock pool account.  |
| popReward   | uint256 | The pop reward.                             |

### removePopAddress (0x36d7dd8e)

```solidity
function removePopAddress(address addr) external
```

Removes an existing proof_of_performance address.


Parameters:

| Name | Type    | Description                                         |
| :--- | :------ | :-------------------------------------------------- |
| addr | address | Address of proof_of_performance contract to remove. |

### setParams (0x9c3ccc82)

```solidity
function setParams(
    uint256 _epochDurationInSeconds,
    uint32 _rewardDelegatedStakeWeight,
    uint256 _minimumPoolStake,
    uint32 _cobbDouglasAlphaNumerator,
    uint32 _cobbDouglasAlphaDenominator
) external
```

Set all configurable parameters at once.


Parameters:

| Name                         | Type    | Description                                                      |
| :--------------------------- | :------ | :--------------------------------------------------------------- |
| _epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                  |
| _rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm.  |
| _minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.   |
| _cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                         |
| _cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                       |

### stake (0xa694fc3a)

```solidity
function stake(uint256 amount) external
```

Stake GRG tokens. Tokens are deposited into the GRG Vault.

Unstake to retrieve the GRG. Stake is in the 'Active' status.


Parameters:

| Name   | Type    | Description      |
| :----- | :------ | :--------------- |
| amount | uint256 | of GRG to stake. |

### unstake (0x2e17de78)

```solidity
function unstake(uint256 amount) external
```

Unstake. Tokens are withdrawn from the GRG Vault and returned to the staker.

Stake must be in the 'undelegated' status in both the current and next epoch in order to be unstaked.


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| amount | uint256 | of GRG to unstake. |

### withdrawDelegatorRewards (0xb510879f)

```solidity
function withdrawDelegatorRewards(bytes32 poolId) external
```

Withdraws the caller's GRG rewards that have accumulated until the last epoch.


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| poolId | bytes32 | Unique id of pool. |

### computeRewardBalanceOfDelegator (0xe907f003)

```solidity
function computeRewardBalanceOfDelegator(
    bytes32 poolId,
    address member
) external view returns (uint256 reward)
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

### computeRewardBalanceOfOperator (0xbb7ef7e0)

```solidity
function computeRewardBalanceOfOperator(
    bytes32 poolId
) external view returns (uint256 reward)
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

### getCurrentEpochEarliestEndTimeInSeconds (0xb2baa33e)

```solidity
function getCurrentEpochEarliestEndTimeInSeconds()
    external
    view
    returns (uint256)
```

Returns the earliest end time in seconds of this epoch.

The next epoch can begin once this time is reached.

Epoch period = [startTimeInSeconds..endTimeInSeconds)


Return values:

| Name | Type    | Description      |
| :--- | :------ | :--------------- |
| [0]  | uint256 | Time in seconds. |

### getGlobalStakeByStatus (0xe804d0a4)

```solidity
function getGlobalStakeByStatus(
    IStructs.StakeStatus stakeStatus
) external view returns (IStructs.StoredBalance memory balance)
```

Gets global stake for a given status.


Parameters:

| Name        | Type                      | Description               |
| :---------- | :------------------------ | :------------------------ |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED  |


Return values:

| Name    | Type                          | Description                    |
| :------ | :---------------------------- | :----------------------------- |
| balance | struct IStructs.StoredBalance | Global stake for given status. |

### getOwnerStakeByStatus (0x44a6958b)

```solidity
function getOwnerStakeByStatus(
    address staker,
    IStructs.StakeStatus stakeStatus
) external view returns (IStructs.StoredBalance memory balance)
```

Gets an owner's stake balances by status.


Parameters:

| Name        | Type                      | Description               |
| :---------- | :------------------------ | :------------------------ |
| staker      | address                   | Owner of stake.           |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED  |


Return values:

| Name    | Type                          | Description                              |
| :------ | :---------------------------- | :--------------------------------------- |
| balance | struct IStructs.StoredBalance | Owner's stake balances for given status. |

### getTotalStake (0x1e7ff8f6)

```solidity
function getTotalStake(address staker) external view returns (uint256)
```

Returns the total stake for a given staker.


Parameters:

| Name   | Type    | Description |
| :----- | :------ | :---------- |
| staker | address | of stake.   |


Return values:

| Name | Type    | Description                   |
| :--- | :------ | :---------------------------- |
| [0]  | uint256 | Total GRG staked by `staker`. |

### getParams (0x5e615a6b)

```solidity
function getParams()
    external
    view
    returns (
        uint256 _epochDurationInSeconds,
        uint32 _rewardDelegatedStakeWeight,
        uint256 _minimumPoolStake,
        uint32 _cobbDouglasAlphaNumerator,
        uint32 _cobbDouglasAlphaDenominator
    )
```

Retrieves all configurable parameter values.


Return values:

| Name                         | Type    | Description                                                      |
| :--------------------------- | :------ | :--------------------------------------------------------------- |
| _epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                  |
| _rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm.  |
| _minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.   |
| _cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                         |
| _cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                       |

### getStakeDelegatedToPoolByOwner (0xf252b7a1)

```solidity
function getStakeDelegatedToPoolByOwner(
    address staker,
    bytes32 poolId
) external view returns (IStructs.StoredBalance memory balance)
```

Returns stake delegated to pool by staker.


Parameters:

| Name   | Type    | Description         |
| :----- | :------ | :------------------ |
| staker | address | of stake.           |
| poolId | bytes32 | Unique Id of pool.  |


Return values:

| Name    | Type                          | Description                        |
| :------ | :---------------------------- | :--------------------------------- |
| balance | struct IStructs.StoredBalance | Stake delegated to pool by staker. |

### getStakingPool (0x4bcc3f67)

```solidity
function getStakingPool(
    bytes32 poolId
) external view returns (IStructs.Pool memory)
```

Returns a staking pool


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| poolId | bytes32 | Unique id of pool. |

### getStakingPoolStatsThisEpoch (0x46b97959)

```solidity
function getStakingPoolStatsThisEpoch(
    bytes32 poolId
) external view returns (IStructs.PoolStats memory)
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

### getTotalStakeDelegatedToPool (0x3e4ad732)

```solidity
function getTotalStakeDelegatedToPool(
    bytes32 poolId
) external view returns (IStructs.StoredBalance memory balance)
```

Returns the total stake delegated to a specific staking pool, across all members.


Parameters:

| Name   | Type    | Description         |
| :----- | :------ | :------------------ |
| poolId | bytes32 | Unique Id of pool.  |


Return values:

| Name    | Type                          | Description                    |
| :------ | :---------------------------- | :----------------------------- |
| balance | struct IStructs.StoredBalance | Total stake delegated to pool. |

### getGrgContract (0xef4ba680)

```solidity
function getGrgContract() external view returns (IRigoToken)
```

An overridable way to access the deployed GRG contract.

Must be view to allow overrides to access state.


Return values:

| Name | Type                | Description                |
| :--- | :------------------ | :------------------------- |
| [0]  | contract IRigoToken | The GRG contract instance. |

### getGrgVault (0xe0822db7)

```solidity
function getGrgVault() external view returns (IGrgVault)
```

An overridable way to access the deployed grgVault.

Must be view to allow overrides to access state.


Return values:

| Name | Type               | Description             |
| :--- | :----------------- | :---------------------- |
| [0]  | contract IGrgVault | The GRG vault contract. |

### getPoolRegistry (0x7a9bd5e4)

```solidity
function getPoolRegistry() external view returns (IPoolRegistry)
```

An overridable way to access the deployed rigoblock pool registry.

Must be view to allow overrides to access state.


Return values:

| Name | Type                   | Description                 |
| :--- | :--------------------- | :-------------------------- |
| [0]  | contract IPoolRegistry | The pool registry contract. |
