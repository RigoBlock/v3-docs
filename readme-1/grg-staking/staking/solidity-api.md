# Solidity API

## Staking

### constructor

```solidity
constructor(address grgVault, address poolRegistry, address rigoToken) public
```

Setting owner to null address prevents admin direct calls to implementation.

_Initializing immutable implementation address is used to allow delegatecalls only. Direct calls to the implementation contract are effectively locked._

#### Parameters

| Name         | Type    | Description                             |
| ------------ | ------- | --------------------------------------- |
| grgVault     | address | Address of the Grg vault.               |
| poolRegistry | address | Address of the RigoBlock pool registry. |
| rigoToken    | address | Address of the Grg token.               |

### init

```solidity
function init() public
```

Initialize storage owned by this contract.

_This function should not be called directly. The StakingProxy contract will call it in `attachStakingContract()`._

## MixinConstants

### \_PPM\_DENOMINATOR

```solidity
uint32 _PPM_DENOMINATOR
```

### \_NIL\_POOL\_ID

```solidity
bytes32 _NIL_POOL_ID
```

### \_NIL\_ADDRESS

```solidity
address _NIL_ADDRESS
```

### \_MIN\_TOKEN\_VALUE

```solidity
uint256 _MIN_TOKEN_VALUE
```

## MixinDeploymentConstants

### constructor

```solidity
constructor(address grgVault, address poolRegistry, address rigoToken) internal
```

### \_implementation

```solidity
address _implementation
```

### \_rigoToken

```solidity
address _rigoToken
```

### \_grgVault

```solidity
address _grgVault
```

### \_poolRegistry

```solidity
address _poolRegistry
```

### getGrgContract

```solidity
function getGrgContract() public view virtual returns (contract IRigoToken)
```

An overridable way to access the deployed GRG contract.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type                | Description                |
| ---- | ------------------- | -------------------------- |
| \[0] | contract IRigoToken | The GRG contract instance. |

### getGrgVault

```solidity
function getGrgVault() public view virtual returns (contract IGrgVault)
```

An overridable way to access the deployed grgVault.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type               | Description             |
| ---- | ------------------ | ----------------------- |
| \[0] | contract IGrgVault | The GRG vault contract. |

### getPoolRegistry

```solidity
function getPoolRegistry() public view virtual returns (contract IPoolRegistry)
```

An overridable way to access the deployed rigoblock pool registry.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type                   | Description                 |
| ---- | ---------------------- | --------------------------- |
| \[0] | contract IPoolRegistry | The pool registry contract. |

## MixinStorage

### stakingContract

```solidity
address stakingContract
```

Address of staking contract.

#### Return Values

### \_globalStakeByStatus

```solidity
mapping(uint8 => struct IStructs.StoredBalance) _globalStakeByStatus
```

### \_ownerStakeByStatus

```solidity
mapping(uint8 => mapping(address => struct IStructs.StoredBalance)) _ownerStakeByStatus
```

### \_delegatedStakeToPoolByOwner

```solidity
mapping(address => mapping(bytes32 => struct IStructs.StoredBalance)) _delegatedStakeToPoolByOwner
```

### \_delegatedStakeByPoolId

```solidity
mapping(bytes32 => struct IStructs.StoredBalance) _delegatedStakeByPoolId
```

### poolIdByRbPoolAccount

```solidity
mapping(address => bytes32) poolIdByRbPoolAccount
```

Mapping from RigoBlock pool subaccount to pool Id of rigoblock pool

_0 RigoBlock pool subaccount address._

#### Return Values

### \_poolById

```solidity
mapping(bytes32 => struct IStructs.Pool) _poolById
```

### rewardsByPoolId

```solidity
mapping(bytes32 => uint256) rewardsByPoolId
```

mapping from pool ID to reward balance of members

_0 Pool ID._

#### Return Values

### currentEpoch

```solidity
uint256 currentEpoch
```

The current epoch.

#### Return Values

### currentEpochStartTimeInSeconds

```solidity
uint256 currentEpochStartTimeInSeconds
```

The current epoch start time.

#### Return Values

### \_cumulativeRewardsByPool

```solidity
mapping(bytes32 => mapping(uint256 => struct IStructs.Fraction)) _cumulativeRewardsByPool
```

### \_cumulativeRewardsByPoolLastStored

```solidity
mapping(bytes32 => uint256) _cumulativeRewardsByPoolLastStored
```

### validPops

```solidity
mapping(address => bool) validPops
```

Registered RigoBlock Proof\_of\_Performance contracts, capable of paying protocol fees.

_0 The address to check._

#### Return Values

### epochDurationInSeconds

```solidity
uint256 epochDurationInSeconds
```

Minimum seconds between epochs.

#### Return Values

### rewardDelegatedStakeWeight

```solidity
uint32 rewardDelegatedStakeWeight
```

#### Return Values

### minimumPoolStake

```solidity
uint256 minimumPoolStake
```

Minimum amount of stake required in a pool to collect rewards.

#### Return Values

### cobbDouglasAlphaNumerator

```solidity
uint32 cobbDouglasAlphaNumerator
```

Numerator for cobb douglas alpha factor.

#### Return Values

### cobbDouglasAlphaDenominator

```solidity
uint32 cobbDouglasAlphaDenominator
```

Denominator for cobb douglas alpha factor.

#### Return Values

### poolStatsByEpoch

```solidity
mapping(bytes32 => mapping(uint256 => struct IStructs.PoolStats)) poolStatsByEpoch
```

Stats for each pool that generated fees with sufficient stake to earn rewards.

_See `_minimumPoolStake` in `MixinParams`._

#### Parameters

#### Return Values

### aggregatedStatsByEpoch

```solidity
mapping(uint256 => struct IStructs.AggregatedStats) aggregatedStatsByEpoch
```

Aggregated stats across all pools that generated fees with sufficient stake to earn rewards.

_See `_minimumPoolStake` in MixinParams._

#### Parameters

#### Return Values

### grgReservedForPoolRewards

```solidity
uint256 grgReservedForPoolRewards
```

The GRG balance of this contract that is reserved for pool reward payouts.

#### Return Values

## IGrgVault

### StakingProxySet

```solidity
event StakingProxySet(address stakingProxyAddress)
```

Emmitted whenever a StakingProxy is set in a vault.

#### Parameters

| Name                | Type    | Description                            |
| ------------------- | ------- | -------------------------------------- |
| stakingProxyAddress | address | Address of the staking proxy contract. |

### InCatastrophicFailureMode

```solidity
event InCatastrophicFailureMode(address sender)
```

Emitted when the Staking contract is put into Catastrophic Failure Mode

#### Parameters

| Name   | Type    | Description                      |
| ------ | ------- | -------------------------------- |
| sender | address | Address of sender (`msg.sender`) |

### Deposit

```solidity
event Deposit(address staker, uint256 amount)
```

Emitted when Grg Tokens are deposited into the vault.

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |
| amount | uint256 | of Grg Tokens deposited.   |

### Withdraw

```solidity
event Withdraw(address staker, uint256 amount)
```

Emitted when Grg Tokens are withdrawn from the vault.

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |
| amount | uint256 | of Grg Tokens withdrawn.   |

### GrgProxySet

```solidity
event GrgProxySet(address grgProxyAddress)
```

Emitted whenever the Grg AssetProxy is set.

#### Parameters

| Name            | Type    | Description                        |
| --------------- | ------- | ---------------------------------- |
| grgProxyAddress | address | Address of the Grg transfer proxy. |

### setStakingProxy

```solidity
function setStakingProxy(address stakingProxyAddress) external
```

Sets the address of the StakingProxy contract.

_Note that only the contract staker can call this function._

#### Parameters

| Name                | Type    | Description                        |
| ------------------- | ------- | ---------------------------------- |
| stakingProxyAddress | address | Address of Staking proxy contract. |

### enterCatastrophicFailure

```solidity
function enterCatastrophicFailure() external
```

Vault enters into Catastrophic Failure Mode.

_\*\*\* WARNING - ONCE IN CATOSTROPHIC FAILURE MODE, YOU CAN NEVER GO BACK! \*\*\* Note that only the contract staker can call this function._

### setGrgProxy

```solidity
function setGrgProxy(address grgProxyAddress) external
```

Sets the Grg proxy.

_Note that only the contract staker can call this. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name            | Type    | Description                         |
| --------------- | ------- | ----------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy. |

### depositFrom

```solidity
function depositFrom(address staker, uint256 amount) external
```

Deposit an `amount` of Grg Tokens from `staker` into the vault.

_Note that only the Staking contract can call this. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |
| amount | uint256 | of Grg Tokens to deposit.  |

### withdrawFrom

```solidity
function withdrawFrom(address staker, uint256 amount) external
```

Withdraw an `amount` of Grg Tokens to `staker` from the vault.

_Note that only the Staking contract can call this. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |
| amount | uint256 | of Grg Tokens to withdraw. |

### withdrawAllFrom

```solidity
function withdrawAllFrom(address staker) external returns (uint256)
```

Withdraw ALL Grg Tokens to `staker` from the vault.

_Note that this can only be called when in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |

### balanceOf

```solidity
function balanceOf(address staker) external view returns (uint256)
```

Returns the balance in Grg Tokens of the `staker`

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | Address of the Grg staker. |

#### Return Values

| Name | Type    | Description     |
| ---- | ------- | --------------- |
| \[0] | uint256 | Balance in Grg. |

### balanceOfGrgVault

```solidity
function balanceOfGrgVault() external view returns (uint256)
```

Returns the entire balance of Grg tokens in the vault.

#### Return Values

| Name | Type    | Description     |
| ---- | ------- | --------------- |
| \[0] | uint256 | Balance in Grg. |

## IStaking

### addPopAddress

```solidity
function addPopAddress(address addr) external
```

Adds a new proof\_of\_performance address.

#### Parameters

| Name | Type    | Description                                        |
| ---- | ------- | -------------------------------------------------- |
| addr | address | Address of proof\_of\_performance contract to add. |

### createStakingPool

```solidity
function createStakingPool(address rigoblockPoolAddress) external returns (bytes32 poolId)
```

Create a new staking pool. The sender will be the staking pal of this pool.

_Note that a staking pal must be payable. When governance updates registry address, pools must be migrated to new registry, or this contract must query from both._

#### Parameters

| Name                 | Type    | Description                                                                  |
| -------------------- | ------- | ---------------------------------------------------------------------------- |
| rigoblockPoolAddress | address | Adds rigoblock pool to the created staking pool for convenience if non-null. |

#### Return Values

| Name   | Type    | Description                                 |
| ------ | ------- | ------------------------------------------- |
| poolId | bytes32 | The unique pool id generated for this pool. |

### setStakingPalAddress

```solidity
function setStakingPalAddress(bytes32 poolId, address newStakingPalAddress) external
```

Allows the operator to update the staking pal address.

#### Parameters

| Name                 | Type    | Description                     |
| -------------------- | ------- | ------------------------------- |
| poolId               | bytes32 | Unique id of pool.              |
| newStakingPalAddress | address | Address of the new staking pal. |

### decreaseStakingPoolOperatorShare

```solidity
function decreaseStakingPoolOperatorShare(bytes32 poolId, uint32 newOperatorShare) external
```

Decreases the operator share for the given pool (i.e. increases pool rewards for members).

#### Parameters

| Name             | Type    | Description                                                          |
| ---------------- | ------- | -------------------------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                                   |
| newOperatorShare | uint32  | The newly decreased percentage of any rewards owned by the operator. |

### endEpoch

```solidity
function endEpoch() external returns (uint256 numPoolsToFinalize)
```

Begins a new epoch, preparing the prior one for finalization.

_Throws if not enough time has passed between epochs or if the previous epoch was not fully finalized._

#### Return Values

| Name               | Type    | Description                      |
| ------------------ | ------- | -------------------------------- |
| numPoolsToFinalize | uint256 | The number of unfinalized pools. |

### finalizePool

```solidity
function finalizePool(bytes32 poolId) external
```

Instantly finalizes a single pool that earned rewards in the previous epoch,

_crediting it rewards for members and withdrawing operator's rewards as GRG. This can be called by internal functions that need to finalize a pool immediately. Does nothing if the pool is already finalized or did not earn rewards in the previous epoch._

#### Parameters

| Name   | Type    | Description              |
| ------ | ------- | ------------------------ |
| poolId | bytes32 | The pool ID to finalize. |

### init

```solidity
function init() external
```

Initialize storage owned by this contract.

_This function should not be called directly. The StakingProxy contract will call it in `attachStakingContract()`._

### moveStake

```solidity
function moveStake(struct IStructs.StakeInfo from, struct IStructs.StakeInfo to, uint256 amount) external
```

Moves stake between statuses: 'undelegated' or 'delegated'.

_Delegated stake can also be moved between pools. This change comes into effect next epoch._

#### Parameters

| Name   | Type                      | Description                  |
| ------ | ------------------------- | ---------------------------- |
| from   | struct IStructs.StakeInfo | Status to move stake out of. |
| to     | struct IStructs.StakeInfo | Status to move stake into.   |
| amount | uint256                   | Amount of stake to move.     |

### creditPopReward

```solidity
function creditPopReward(address poolAccount, uint256 popReward) external payable
```

Credits the value of a pool's pop reward.

_Only a known RigoBlock pop can call this method. See (MixinPopManager)._

#### Parameters

| Name        | Type    | Description                                |
| ----------- | ------- | ------------------------------------------ |
| poolAccount | address | The address of the rigoblock pool account. |
| popReward   | uint256 | The pop reward.                            |

### removePopAddress

```solidity
function removePopAddress(address addr) external
```

Removes an existing proof\_of\_performance address.

#### Parameters

| Name | Type    | Description                                           |
| ---- | ------- | ----------------------------------------------------- |
| addr | address | Address of proof\_of\_performance contract to remove. |

### setParams

```solidity
function setParams(uint256 _epochDurationInSeconds, uint32 _rewardDelegatedStakeWeight, uint256 _minimumPoolStake, uint32 _cobbDouglasAlphaNumerator, uint32 _cobbDouglasAlphaDenominator) external
```

Set all configurable parameters at once.

#### Parameters

| Name                          | Type    | Description                                                     |
| ----------------------------- | ------- | --------------------------------------------------------------- |
| \_epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| \_rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| \_minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| \_cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                        |
| \_cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                      |

### stake

```solidity
function stake(uint256 amount) external
```

Stake GRG tokens. Tokens are deposited into the GRG Vault.

_Unstake to retrieve the GRG. Stake is in the 'Active' status._

#### Parameters

| Name   | Type    | Description      |
| ------ | ------- | ---------------- |
| amount | uint256 | of GRG to stake. |

### unstake

```solidity
function unstake(uint256 amount) external
```

Unstake. Tokens are withdrawn from the GRG Vault and returned to the staker.

_Stake must be in the 'undelegated' status in both the current and next epoch in order to be unstaked._

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| amount | uint256 | of GRG to unstake. |

### withdrawDelegatorRewards

```solidity
function withdrawDelegatorRewards(bytes32 poolId) external
```

Withdraws the caller's GRG rewards that have accumulated until the last epoch.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### computeRewardBalanceOfDelegator

```solidity
function computeRewardBalanceOfDelegator(bytes32 poolId, address member) external view returns (uint256 reward)
```

Computes the reward balance in GRG of a specific member of a pool.

#### Parameters

| Name   | Type    | Description             |
| ------ | ------- | ----------------------- |
| poolId | bytes32 | Unique id of pool.      |
| member | address | The member of the pool. |

#### Return Values

| Name   | Type    | Description     |
| ------ | ------- | --------------- |
| reward | uint256 | Balance in GRG. |

### computeRewardBalanceOfOperator

```solidity
function computeRewardBalanceOfOperator(bytes32 poolId) external view returns (uint256 reward)
```

Computes the reward balance in GRG of the operator of a pool.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

#### Return Values

| Name   | Type    | Description     |
| ------ | ------- | --------------- |
| reward | uint256 | Balance in GRG. |

### getCurrentEpochEarliestEndTimeInSeconds

```solidity
function getCurrentEpochEarliestEndTimeInSeconds() external view returns (uint256)
```

Returns the earliest end time in seconds of this epoch.

_The next epoch can begin once this time is reached. Epoch period = \[startTimeInSeconds..endTimeInSeconds)_

#### Return Values

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| \[0] | uint256 | Time in seconds. |

### getGlobalStakeByStatus

```solidity
function getGlobalStakeByStatus(enum IStructs.StakeStatus stakeStatus) external view returns (struct IStructs.StoredBalance balance)
```

Gets global stake for a given status.

#### Parameters

| Name        | Type                      | Description              |
| ----------- | ------------------------- | ------------------------ |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED |

#### Return Values

| Name    | Type                          | Description                    |
| ------- | ----------------------------- | ------------------------------ |
| balance | struct IStructs.StoredBalance | Global stake for given status. |

### getOwnerStakeByStatus

```solidity
function getOwnerStakeByStatus(address staker, enum IStructs.StakeStatus stakeStatus) external view returns (struct IStructs.StoredBalance balance)
```

Gets an owner's stake balances by status.

#### Parameters

| Name        | Type                      | Description              |
| ----------- | ------------------------- | ------------------------ |
| staker      | address                   | Owner of stake.          |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED |

#### Return Values

| Name    | Type                          | Description                              |
| ------- | ----------------------------- | ---------------------------------------- |
| balance | struct IStructs.StoredBalance | Owner's stake balances for given status. |

### getTotalStake

```solidity
function getTotalStake(address staker) external view returns (uint256)
```

Returns the total stake for a given staker.

#### Parameters

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| staker | address | of stake.   |

#### Return Values

| Name | Type    | Description                   |
| ---- | ------- | ----------------------------- |
| \[0] | uint256 | Total GRG staked by `staker`. |

### getParams

```solidity
function getParams() external view returns (uint256 _epochDurationInSeconds, uint32 _rewardDelegatedStakeWeight, uint256 _minimumPoolStake, uint32 _cobbDouglasAlphaNumerator, uint32 _cobbDouglasAlphaDenominator)
```

_Retrieves all configurable parameter values._

#### Return Values

| Name                          | Type    | Description                                                     |
| ----------------------------- | ------- | --------------------------------------------------------------- |
| \_epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| \_rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| \_minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| \_cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                        |
| \_cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                      |

### getStakeDelegatedToPoolByOwner

```solidity
function getStakeDelegatedToPoolByOwner(address staker, bytes32 poolId) external view returns (struct IStructs.StoredBalance balance)
```

Returns stake delegated to pool by staker.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| staker | address | of stake.          |
| poolId | bytes32 | Unique Id of pool. |

#### Return Values

| Name    | Type                          | Description                        |
| ------- | ----------------------------- | ---------------------------------- |
| balance | struct IStructs.StoredBalance | Stake delegated to pool by staker. |

### getStakingPool

```solidity
function getStakingPool(bytes32 poolId) external view returns (struct IStructs.Pool)
```

Returns a staking pool

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### getStakingPoolStatsThisEpoch

```solidity
function getStakingPoolStatsThisEpoch(bytes32 poolId) external view returns (struct IStructs.PoolStats)
```

Get stats on a staking pool in this epoch.

#### Parameters

| Name   | Type    | Description       |
| ------ | ------- | ----------------- |
| poolId | bytes32 | Pool Id to query. |

#### Return Values

| Name | Type                      | Description                   |
| ---- | ------------------------- | ----------------------------- |
| \[0] | struct IStructs.PoolStats | PoolStats struct for pool id. |

### getTotalStakeDelegatedToPool

```solidity
function getTotalStakeDelegatedToPool(bytes32 poolId) external view returns (struct IStructs.StoredBalance balance)
```

Returns the total stake delegated to a specific staking pool, across all members.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique Id of pool. |

#### Return Values

| Name    | Type                          | Description                    |
| ------- | ----------------------------- | ------------------------------ |
| balance | struct IStructs.StoredBalance | Total stake delegated to pool. |

### getGrgContract

```solidity
function getGrgContract() external view returns (contract IRigoToken)
```

An overridable way to access the deployed GRG contract.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type                | Description                |
| ---- | ------------------- | -------------------------- |
| \[0] | contract IRigoToken | The GRG contract instance. |

### getGrgVault

```solidity
function getGrgVault() external view returns (contract IGrgVault)
```

An overridable way to access the deployed grgVault.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type               | Description             |
| ---- | ------------------ | ----------------------- |
| \[0] | contract IGrgVault | The GRG vault contract. |

### getPoolRegistry

```solidity
function getPoolRegistry() external view returns (contract IPoolRegistry)
```

An overridable way to access the deployed rigoblock pool registry.

_Must be view to allow overrides to access state._

#### Return Values

| Name | Type                   | Description                 |
| ---- | ---------------------- | --------------------------- |
| \[0] | contract IPoolRegistry | The pool registry contract. |

## IStakingEvents

### Stake

```solidity
event Stake(address staker, uint256 amount)
```

Emitted by MixinStake when GRG is staked.

#### Parameters

| Name   | Type    | Description    |
| ------ | ------- | -------------- |
| staker | address | of GRG.        |
| amount | uint256 | of GRG staked. |

### Unstake

```solidity
event Unstake(address staker, uint256 amount)
```

Emitted by MixinStake when GRG is unstaked.

#### Parameters

| Name   | Type    | Description      |
| ------ | ------- | ---------------- |
| staker | address | of GRG.          |
| amount | uint256 | of GRG unstaked. |

### MoveStake

```solidity
event MoveStake(address staker, uint256 amount, uint8 fromStatus, bytes32 fromPool, uint8 toStatus, bytes32 toPool)
```

Emitted by MixinStake when GRG is unstaked.

#### Parameters

| Name       | Type    | Description      |
| ---------- | ------- | ---------------- |
| staker     | address | of GRG.          |
| amount     | uint256 | of GRG unstaked. |
| fromStatus | uint8   |                  |
| fromPool   | bytes32 |                  |
| toStatus   | uint8   |                  |
| toPool     | bytes32 |                  |

### PopAdded

```solidity
event PopAdded(address exchangeAddress)
```

Emitted by MixinExchangeManager when an exchange is added.

#### Parameters

| Name            | Type    | Description              |
| --------------- | ------- | ------------------------ |
| exchangeAddress | address | Address of new exchange. |

### PopRemoved

```solidity
event PopRemoved(address exchangeAddress)
```

Emitted by MixinExchangeManager when an exchange is removed.

#### Parameters

| Name            | Type    | Description                  |
| --------------- | ------- | ---------------------------- |
| exchangeAddress | address | Address of removed exchange. |

### StakingPoolEarnedRewardsInEpoch

```solidity
event StakingPoolEarnedRewardsInEpoch(uint256 epoch, bytes32 poolId)
```

Emitted by MixinExchangeFees when a pool starts earning rewards in an epoch.

#### Parameters

| Name   | Type    | Description                                 |
| ------ | ------- | ------------------------------------------- |
| epoch  | uint256 | The epoch in which the pool earned rewards. |
| poolId | bytes32 | The ID of the pool.                         |

### EpochEnded

```solidity
event EpochEnded(uint256 epoch, uint256 numPoolsToFinalize, uint256 rewardsAvailable, uint256 totalFeesCollected, uint256 totalWeightedStake)
```

Emitted by MixinFinalizer when an epoch has ended.

#### Parameters

| Name               | Type    | Description                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| epoch              | uint256 | The epoch that ended.                                                     |
| numPoolsToFinalize | uint256 | Number of pools that earned rewards during `epoch` and must be finalized. |
| rewardsAvailable   | uint256 | Rewards available to all pools that earned rewards during `epoch`.        |
| totalFeesCollected | uint256 | Total fees collected across all pools that earned rewards during `epoch`. |
| totalWeightedStake | uint256 | Total weighted stake across all pools that earned rewards during `epoch`. |

### EpochFinalized

```solidity
event EpochFinalized(uint256 epoch, uint256 rewardsPaid, uint256 rewardsRemaining)
```

Emitted by MixinFinalizer when an epoch is fully finalized.

#### Parameters

| Name             | Type    | Description                       |
| ---------------- | ------- | --------------------------------- |
| epoch            | uint256 | The epoch being finalized.        |
| rewardsPaid      | uint256 | Total amount of rewards paid out. |
| rewardsRemaining | uint256 | Rewards left over.                |

### RewardsPaid

```solidity
event RewardsPaid(uint256 epoch, bytes32 poolId, uint256 operatorReward, uint256 membersReward)
```

Emitted by MixinFinalizer when rewards are paid out to a pool.

#### Parameters

| Name           | Type    | Description                               |
| -------------- | ------- | ----------------------------------------- |
| epoch          | uint256 | The epoch when the rewards were paid out. |
| poolId         | bytes32 | The pool's ID.                            |
| operatorReward | uint256 | Amount of reward paid to pool operator.   |
| membersReward  | uint256 | Amount of reward paid to pool members.    |

### ParamsSet

```solidity
event ParamsSet(uint256 epochDurationInSeconds, uint32 rewardDelegatedStakeWeight, uint256 minimumPoolStake, uint256 cobbDouglasAlphaNumerator, uint256 cobbDouglasAlphaDenominator)
```

Emitted whenever staking parameters are changed via the `setParams()` function.

#### Parameters

| Name                        | Type    | Description                                                     |
| --------------------------- | ------- | --------------------------------------------------------------- |
| epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| cobbDouglasAlphaNumerator   | uint256 | Numerator for cobb douglas alpha factor.                        |
| cobbDouglasAlphaDenominator | uint256 | Denominator for cobb douglas alpha factor.                      |

### StakingPoolCreated

```solidity
event StakingPoolCreated(bytes32 poolId, address operator, uint32 operatorShare)
```

Emitted by MixinStakingPool when a new pool is created.

#### Parameters

| Name          | Type    | Description                                         |
| ------------- | ------- | --------------------------------------------------- |
| poolId        | bytes32 | Unique id generated for pool.                       |
| operator      | address | The operator (creator) of pool.                     |
| operatorShare | uint32  | The share of rewards given to the operator, in ppm. |

### RbPoolStakingPoolSet

```solidity
event RbPoolStakingPoolSet(address rbPoolAddress, bytes32 poolId)
```

Emitted by MixinStakingPool when a rigoblock pool is added to its staking pool.

#### Parameters

| Name          | Type    | Description                    |
| ------------- | ------- | ------------------------------ |
| rbPoolAddress | address | Adress of maker added to pool. |
| poolId        | bytes32 | Unique id of pool.             |

### OperatorShareDecreased

```solidity
event OperatorShareDecreased(bytes32 poolId, uint32 oldOperatorShare, uint32 newOperatorShare)
```

Emitted when a staking pool's operator share is decreased.

#### Parameters

| Name             | Type    | Description                                         |
| ---------------- | ------- | --------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                  |
| oldOperatorShare | uint32  | Previous share of rewards owned by operator.        |
| newOperatorShare | uint32  | Newly decreased share of rewards owned by operator. |

### GrgMintEvent

```solidity
event GrgMintEvent(uint256 grgAmount)
```

Emitted when an inflation mint call is executed successfully.

#### Parameters

| Name      | Type    | Description                                       |
| --------- | ------- | ------------------------------------------------- |
| grgAmount | uint256 | Amount of GRG tokens minted to the staking proxy. |

### CatchStringEvent

```solidity
event CatchStringEvent(string reason)
```

Emitted whenever an inflation mint call is reverted.

#### Parameters

| Name   | Type   | Description                   |
| ------ | ------ | ----------------------------- |
| reason | string | String of the revert message. |

### ReturnDataEvent

```solidity
event ReturnDataEvent(bytes reason)
```

Emitted to catch any other inflation mint call fail.

#### Parameters

| Name   | Type  | Description                               |
| ------ | ----- | ----------------------------------------- |
| reason | bytes | Bytes output of the reverted transaction. |

## IStakingProxy

### StakingContractAttachedToProxy

```solidity
event StakingContractAttachedToProxy(address newStakingContractAddress)
```

Emitted by StakingProxy when a staking contract is attached.

#### Parameters

| Name                      | Type    | Description                                 |
| ------------------------- | ------- | ------------------------------------------- |
| newStakingContractAddress | address | Address of newly attached staking contract. |

### StakingContractDetachedFromProxy

```solidity
event StakingContractDetachedFromProxy()
```

Emitted by StakingProxy when a staking contract is detached.

### attachStakingContract

```solidity
function attachStakingContract(address stakingImplementation) external
```

Attach a staking contract; future calls will be delegated to the staking contract.

_Note that this is callable only by an authorized address._

#### Parameters

| Name                  | Type    | Description                  |
| --------------------- | ------- | ---------------------------- |
| stakingImplementation | address | Address of staking contract. |

### detachStakingContract

```solidity
function detachStakingContract() external
```

Detach the current staking contract.

_Note that this is callable only by an authorized address._

### batchExecute

```solidity
function batchExecute(bytes[] data) external returns (bytes[] batchReturnData)
```

Batch executes a series of calls to the staking contract.

#### Parameters

| Name | Type     | Description                                                                             |
| ---- | -------- | --------------------------------------------------------------------------------------- |
| data | bytes\[] | An array of data that encodes a sequence of functions to call in the staking contracts. |

### assertValidStorageParams

```solidity
function assertValidStorageParams() external view
```

Asserts initialziation parameters are correct.

_Asserts that an epoch is between 5 and 30 days long. Asserts that 0 < cobb douglas alpha value <= 1. Asserts that a stake weight is <= 100%. Asserts that pools allow >= 1 maker. Asserts that all addresses are initialized._

## IStorage

### stakingContract

```solidity
function stakingContract() external view returns (address)
```

Address of staking contract.

#### Return Values

| Name | Type    | Description                                      |
| ---- | ------- | ------------------------------------------------ |
| \[0] | address | stakingContract Address of the staking contract. |

### poolIdByRbPoolAccount

```solidity
function poolIdByRbPoolAccount(address) external view returns (bytes32)
```

Mapping from RigoBlock pool subaccount to pool Id of rigoblock pool

_0 RigoBlock pool subaccount address._

#### Return Values

| Name | Type    | Description    |
| ---- | ------- | -------------- |
| \[0] | bytes32 | 0 The pool ID. |

### rewardsByPoolId

```solidity
function rewardsByPoolId(bytes32) external view returns (uint256)
```

mapping from pool ID to reward balance of members

_0 Pool ID._

#### Return Values

| Name | Type    | Description                                         |
| ---- | ------- | --------------------------------------------------- |
| \[0] | uint256 | 0 The total reward balance of members in this pool. |

### currentEpoch

```solidity
function currentEpoch() external view returns (uint256)
```

The current epoch.

#### Return Values

| Name | Type    | Description                                   |
| ---- | ------- | --------------------------------------------- |
| \[0] | uint256 | currentEpoch The number of the current epoch. |

### currentEpochStartTimeInSeconds

```solidity
function currentEpochStartTimeInSeconds() external view returns (uint256)
```

The current epoch start time.

#### Return Values

| Name | Type    | Description                                             |
| ---- | ------- | ------------------------------------------------------- |
| \[0] | uint256 | currentEpochStartTimeInSeconds Timestamp of start time. |

### validPops

```solidity
function validPops(address popAddress) external view returns (bool)
```

Registered RigoBlock Proof\_of\_Performance contracts, capable of paying protocol fees.

_0 The address to check._

#### Return Values

| Name | Type | Description                                                   |
| ---- | ---- | ------------------------------------------------------------- |
| \[0] | bool | 0 Whether the address is a registered proof\_of\_performance. |

### epochDurationInSeconds

```solidity
function epochDurationInSeconds() external view returns (uint256)
```

Minimum seconds between epochs.

#### Return Values

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| \[0] | uint256 | epochDurationInSeconds Number of seconds. |

### rewardDelegatedStakeWeight

```solidity
function rewardDelegatedStakeWeight() external view returns (uint32)
```

#### Return Values

| Name | Type   | Description                                              |
| ---- | ------ | -------------------------------------------------------- |
| \[0] | uint32 | rewardDelegatedStakeWeight Number in units of a million. |

### minimumPoolStake

```solidity
function minimumPoolStake() external view returns (uint256)
```

Minimum amount of stake required in a pool to collect rewards.

#### Return Values

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| \[0] | uint256 | minimumPoolStake Minimum amount required. |

### cobbDouglasAlphaNumerator

```solidity
function cobbDouglasAlphaNumerator() external view returns (uint32)
```

Numerator for cobb douglas alpha factor.

#### Return Values

| Name | Type   | Description                                        |
| ---- | ------ | -------------------------------------------------- |
| \[0] | uint32 | cobbDouglasAlphaNumerator Number of the numerator. |

### cobbDouglasAlphaDenominator

```solidity
function cobbDouglasAlphaDenominator() external view returns (uint32)
```

Denominator for cobb douglas alpha factor.

#### Return Values

| Name | Type   | Description                                            |
| ---- | ------ | ------------------------------------------------------ |
| \[0] | uint32 | cobbDouglasAlphaDenominator Number of the denominator. |

### poolStatsByEpoch

```solidity
function poolStatsByEpoch(bytes32 key, uint256 epoch) external view returns (uint256 feesCollected, uint256 weightedStake, uint256 membersStake)
```

Stats for each pool that generated fees with sufficient stake to earn rewards.

_See `_minimumPoolStake` in `MixinParams`._

#### Parameters

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| key   | bytes32 | Pool ID.      |
| epoch | uint256 | Epoch number. |

#### Return Values

| Name          | Type    | Description                        |
| ------------- | ------- | ---------------------------------- |
| feesCollected | uint256 | Amount of fees collected in epoch. |
| weightedStake | uint256 | Weighted stake per million.        |
| membersStake  | uint256 | Members stake per million.         |

### aggregatedStatsByEpoch

```solidity
function aggregatedStatsByEpoch(uint256 epoch) external view returns (uint256 rewardsAvailable, uint256 numPoolsToFinalize, uint256 totalFeesCollected, uint256 totalWeightedStake, uint256 totalRewardsFinalized)
```

Aggregated stats across all pools that generated fees with sufficient stake to earn rewards.

_See `_minimumPoolStake` in MixinParams._

#### Parameters

| Name  | Type    | Description   |
| ----- | ------- | ------------- |
| epoch | uint256 | Epoch number. |

#### Return Values

| Name                  | Type    | Description                                                                  |
| --------------------- | ------- | ---------------------------------------------------------------------------- |
| rewardsAvailable      | uint256 | Rewards (GRG) available to the epoch being finalized (the previous epoch).   |
| numPoolsToFinalize    | uint256 | The number of pools that have yet to be finalized through `finalizePools()`. |
| totalFeesCollected    | uint256 | The total fees collected for the epoch being finalized.                      |
| totalWeightedStake    | uint256 | The total fees collected for the epoch being finalized.                      |
| totalRewardsFinalized | uint256 | Amount of rewards that have been paid during finalization.                   |

### grgReservedForPoolRewards

```solidity
function grgReservedForPoolRewards() external view returns (uint256)
```

The GRG balance of this contract that is reserved for pool reward payouts.

#### Return Values

| Name | Type    | Description                                                      |
| ---- | ------- | ---------------------------------------------------------------- |
| \[0] | uint256 | grgReservedForPoolRewards Number of tokens reserved for rewards. |

## IStorageInit

### init

```solidity
function init() external
```

Initialize storage owned by this contract.

## IStructs

### PoolStats

```solidity
struct PoolStats {
  uint256 feesCollected;
  uint256 weightedStake;
  uint256 membersStake;
}
```

### AggregatedStats

```solidity
struct AggregatedStats {
  uint256 rewardsAvailable;
  uint256 numPoolsToFinalize;
  uint256 totalFeesCollected;
  uint256 totalWeightedStake;
  uint256 totalRewardsFinalized;
}
```

### StoredBalance

```solidity
struct StoredBalance {
  uint64 currentEpoch;
  uint96 currentEpochBalance;
  uint96 nextEpochBalance;
}
```

### StakeStatus

```solidity
enum StakeStatus {
  UNDELEGATED,
  DELEGATED
}
```

### StakeInfo

```solidity
struct StakeInfo {
  enum IStructs.StakeStatus status;
  bytes32 poolId;
}
```

### Fraction

```solidity
struct Fraction {
  uint256 numerator;
  uint256 denominator;
}
```

### Pool

```solidity
struct Pool {
  address operator;
  address stakingPal;
  uint32 operatorShare;
  uint32 stakingPalShare;
}
```

## LibCobbDouglas

### cobbDouglas

```solidity
function cobbDouglas(uint256 totalRewards, uint256 fees, uint256 totalFees, uint256 stake, uint256 totalStake, uint32 alphaNumerator, uint32 alphaDenominator) internal pure returns (uint256 rewards)
```

_The cobb-douglas function used to compute fee-based rewards for staking pools in a given epoch. This function does not perform bounds checking on the inputs, but the following conditions need to be true: 0 <= fees / totalFees <= 1 0 <= stake / totalStake <= 1 0 <= alphaNumerator / alphaDenominator <= 1_

#### Parameters

| Name             | Type    | Description                                                |
| ---------------- | ------- | ---------------------------------------------------------- |
| totalRewards     | uint256 | collected over an epoch.                                   |
| fees             | uint256 | Fees attributed to the the staking pool.                   |
| totalFees        | uint256 | Total fees collected across all pools that earned rewards. |
| stake            | uint256 | Stake attributed to the staking pool.                      |
| totalStake       | uint256 | Total stake across all pools that earned rewards.          |
| alphaNumerator   | uint32  | Numerator of `alpha` in the cobb-douglas function.         |
| alphaDenominator | uint32  | Denominator of `alpha` in the cobb-douglas function.       |

#### Return Values

| Name    | Type    | Description                       |
| ------- | ------- | --------------------------------- |
| rewards | uint256 | Rewards owed to the staking pool. |

## LibFixedMath

_Signed, fixed-point, 127-bit precision math library._

### FIXED\_1

```solidity
int256 FIXED_1
```

### MIN\_FIXED\_VAL

```solidity
int256 MIN_FIXED_VAL
```

### FIXED\_1\_SQUARED

```solidity
int256 FIXED_1_SQUARED
```

### LN\_MAX\_VAL

```solidity
int256 LN_MAX_VAL
```

### LN\_MIN\_VAL

```solidity
int256 LN_MIN_VAL
```

### EXP\_MAX\_VAL

```solidity
int256 EXP_MAX_VAL
```

### EXP\_MIN\_VAL

```solidity
int256 EXP_MIN_VAL
```

### mul

```solidity
function mul(int256 a, int256 b) internal pure returns (int256 c)
```

_Returns the multiplication of two fixed point numbers, reverting on overflow._

### div

```solidity
function div(int256 a, int256 b) internal pure returns (int256 c)
```

_Returns the division of two fixed point numbers._

### mulDiv

```solidity
function mulDiv(int256 a, int256 n, int256 d) internal pure returns (int256 c)
```

_Performs (a \* n) / d, without scaling for precision._

### uintMul

```solidity
function uintMul(int256 f, uint256 u) internal pure returns (uint256)
```

_Returns the unsigned integer result of multiplying a fixed-point number with an integer, reverting if the multiplication overflows. Negative results are clamped to zero._

### toFixed

```solidity
function toFixed(uint256 n, uint256 d) internal pure returns (int256 f)
```

_Convert unsigned `n` / `d` to a fixed-point number. Reverts if `n` / `d` is too large to fit in a fixed-point number._

### ln

```solidity
function ln(int256 x) internal pure returns (int256 r)
```

_Get the natural logarithm of a fixed-point number 0 < `x` <= LN\_MAX\_VAL_

### exp

```solidity
function exp(int256 x) internal pure returns (int256 r)
```

_Compute the natural exponent for a fixed-point number EXP\_MIN\_VAL <= `x` <= 1_

### \_mul

```solidity
function _mul(int256 a, int256 b) private pure returns (int256 c)
```

_Returns the multiplication two numbers, reverting on overflow._

### \_div

```solidity
function _div(int256 a, int256 b) private pure returns (int256 c)
```

_Returns the division of two numbers, reverting on division by zero._

## LibSafeDowncast

### downcastToUint96

```solidity
function downcastToUint96(uint256 a) internal pure returns (uint96 b)
```

_Safely downcasts to a uint96 Note that this reverts if the input value is too large._

### downcastToUint64

```solidity
function downcastToUint64(uint256 a) internal pure returns (uint64 b)
```

_Safely downcasts to a uint64 Note that this reverts if the input value is too large._

## MixinPopManager

### addPopAddress

```solidity
function addPopAddress(address addr) external
```

Adds a new proof\_of\_performance address.

#### Parameters

| Name | Type    | Description                                        |
| ---- | ------- | -------------------------------------------------- |
| addr | address | Address of proof\_of\_performance contract to add. |

### removePopAddress

```solidity
function removePopAddress(address addr) external
```

Removes an existing proof\_of\_performance address.

#### Parameters

| Name | Type    | Description                                           |
| ---- | ------- | ----------------------------------------------------- |
| addr | address | Address of proof\_of\_performance contract to remove. |

## MixinPopRewards

### onlyPop

```solidity
modifier onlyPop()
```

_Asserts that the call is coming from a valid pop._

### creditPopReward

```solidity
function creditPopReward(address poolAccount, uint256 popReward) external payable
```

Credits the value of a pool's pop reward.

_Only a known RigoBlock pop can call this method. See (MixinPopManager)._

#### Parameters

| Name        | Type    | Description                                |
| ----------- | ------- | ------------------------------------------ |
| poolAccount | address | The address of the rigoblock pool account. |
| popReward   | uint256 | The pop reward.                            |

### getStakingPoolStatsThisEpoch

```solidity
function getStakingPoolStatsThisEpoch(bytes32 poolId) external view returns (struct IStructs.PoolStats)
```

Get stats on a staking pool in this epoch.

#### Parameters

| Name   | Type    | Description       |
| ------ | ------- | ----------------- |
| poolId | bytes32 | Pool Id to query. |

#### Return Values

| Name | Type                      | Description                   |
| ---- | ------------------------- | ----------------------------- |
| \[0] | struct IStructs.PoolStats | PoolStats struct for pool id. |

### \_computeMembersAndWeightedStake

```solidity
function _computeMembersAndWeightedStake(bytes32 poolId, uint256 totalStake) private view returns (uint256 membersStake, uint256 weightedStake)
```

_Computes the members and weighted stake for a pool at the current epoch._

#### Parameters

| Name       | Type    | Description                           |
| ---------- | ------- | ------------------------------------- |
| poolId     | bytes32 | ID of the pool.                       |
| totalStake | uint256 | Total (unweighted) stake in the pool. |

#### Return Values

| Name          | Type    | Description                     |
| ------------- | ------- | ------------------------------- |
| membersStake  | uint256 | Non-operator stake in the pool. |
| weightedStake | uint256 | Weighted stake of the pool.     |

## MixinStake

### stake

```solidity
function stake(uint256 amount) external
```

Stake GRG tokens. Tokens are deposited into the GRG Vault.

_Unstake to retrieve the GRG. Stake is in the 'Active' status._

#### Parameters

| Name   | Type    | Description      |
| ------ | ------- | ---------------- |
| amount | uint256 | of GRG to stake. |

### unstake

```solidity
function unstake(uint256 amount) external
```

Unstake. Tokens are withdrawn from the GRG Vault and returned to the staker.

_Stake must be in the 'undelegated' status in both the current and next epoch in order to be unstaked._

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| amount | uint256 | of GRG to unstake. |

### moveStake

```solidity
function moveStake(struct IStructs.StakeInfo from, struct IStructs.StakeInfo to, uint256 amount) external
```

Moves stake between statuses: 'undelegated' or 'delegated'.

_Delegated stake can also be moved between pools. This change comes into effect next epoch._

#### Parameters

| Name   | Type                      | Description                  |
| ------ | ------------------------- | ---------------------------- |
| from   | struct IStructs.StakeInfo | Status to move stake out of. |
| to     | struct IStructs.StakeInfo | Status to move stake into.   |
| amount | uint256                   | Amount of stake to move.     |

### \_delegateStake

```solidity
function _delegateStake(bytes32 poolId, address staker, uint256 amount) private
```

_Delegates a owners stake to a staking pool._

#### Parameters

| Name   | Type    | Description                  |
| ------ | ------- | ---------------------------- |
| poolId | bytes32 | Id of pool to delegate to.   |
| staker | address | Owner who wants to delegate. |
| amount | uint256 | Amount of stake to delegate. |

### \_undelegateStake

```solidity
function _undelegateStake(bytes32 poolId, address staker, uint256 amount) private
```

_Un-Delegates a owners stake from a staking pool._

#### Parameters

| Name   | Type    | Description                     |
| ------ | ------- | ------------------------------- |
| poolId | bytes32 | Id of pool to un-delegate from. |
| staker | address | Owner who wants to un-delegate. |
| amount | uint256 | Amount of stake to un-delegate. |

## MixinStakeBalances

### getGlobalStakeByStatus

```solidity
function getGlobalStakeByStatus(enum IStructs.StakeStatus stakeStatus) external view returns (struct IStructs.StoredBalance balance)
```

Gets global stake for a given status.

#### Parameters

| Name        | Type                      | Description              |
| ----------- | ------------------------- | ------------------------ |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED |

#### Return Values

| Name    | Type                          | Description                    |
| ------- | ----------------------------- | ------------------------------ |
| balance | struct IStructs.StoredBalance | Global stake for given status. |

### getOwnerStakeByStatus

```solidity
function getOwnerStakeByStatus(address staker, enum IStructs.StakeStatus stakeStatus) external view returns (struct IStructs.StoredBalance balance)
```

Gets an owner's stake balances by status.

#### Parameters

| Name        | Type                      | Description              |
| ----------- | ------------------------- | ------------------------ |
| staker      | address                   | Owner of stake.          |
| stakeStatus | enum IStructs.StakeStatus | UNDELEGATED or DELEGATED |

#### Return Values

| Name    | Type                          | Description                              |
| ------- | ----------------------------- | ---------------------------------------- |
| balance | struct IStructs.StoredBalance | Owner's stake balances for given status. |

### getTotalStake

```solidity
function getTotalStake(address staker) public view returns (uint256)
```

Returns the total stake for a given staker.

#### Parameters

| Name   | Type    | Description |
| ------ | ------- | ----------- |
| staker | address | of stake.   |

#### Return Values

| Name | Type    | Description                   |
| ---- | ------- | ----------------------------- |
| \[0] | uint256 | Total GRG staked by `staker`. |

### getStakeDelegatedToPoolByOwner

```solidity
function getStakeDelegatedToPoolByOwner(address staker, bytes32 poolId) public view returns (struct IStructs.StoredBalance balance)
```

Returns stake delegated to pool by staker.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| staker | address | of stake.          |
| poolId | bytes32 | Unique Id of pool. |

#### Return Values

| Name    | Type                          | Description                        |
| ------- | ----------------------------- | ---------------------------------- |
| balance | struct IStructs.StoredBalance | Stake delegated to pool by staker. |

### getTotalStakeDelegatedToPool

```solidity
function getTotalStakeDelegatedToPool(bytes32 poolId) public view returns (struct IStructs.StoredBalance balance)
```

Returns the total stake delegated to a specific staking pool, across all members.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique Id of pool. |

#### Return Values

| Name    | Type                          | Description                    |
| ------- | ----------------------------- | ------------------------------ |
| balance | struct IStructs.StoredBalance | Total stake delegated to pool. |

## MixinStakeStorage

_This mixin contains logic for managing stake storage._

### \_moveStake

```solidity
function _moveStake(struct IStructs.StoredBalance fromPtr, struct IStructs.StoredBalance toPtr, uint256 amount) internal
```

_Moves stake between states: 'undelegated' or 'delegated'. This change comes into effect next epoch._

#### Parameters

| Name    | Type                          | Description                                  |
| ------- | ----------------------------- | -------------------------------------------- |
| fromPtr | struct IStructs.StoredBalance | pointer to storage location of `from` stake. |
| toPtr   | struct IStructs.StoredBalance | pointer to storage location of `to` stake.   |
| amount  | uint256                       | of stake to move.                            |

### \_loadCurrentBalance

```solidity
function _loadCurrentBalance(struct IStructs.StoredBalance balancePtr) internal view returns (struct IStructs.StoredBalance balance)
```

_Loads a balance from storage and updates its fields to reflect values for the current epoch._

#### Parameters

| Name       | Type                          | Description |
| ---------- | ----------------------------- | ----------- |
| balancePtr | struct IStructs.StoredBalance | to load.    |

#### Return Values

| Name    | Type                          | Description      |
| ------- | ----------------------------- | ---------------- |
| balance | struct IStructs.StoredBalance | current balance. |

### \_increaseCurrentAndNextBalance

```solidity
function _increaseCurrentAndNextBalance(struct IStructs.StoredBalance balancePtr, uint256 amount) internal
```

_Increments both the `current` and `next` fields._

#### Parameters

| Name       | Type                          | Description                 |
| ---------- | ----------------------------- | --------------------------- |
| balancePtr | struct IStructs.StoredBalance | storage pointer to balance. |
| amount     | uint256                       | to mint.                    |

### \_decreaseCurrentAndNextBalance

```solidity
function _decreaseCurrentAndNextBalance(struct IStructs.StoredBalance balancePtr, uint256 amount) internal
```

_Decrements both the `current` and `next` fields._

#### Parameters

| Name       | Type                          | Description                 |
| ---------- | ----------------------------- | --------------------------- |
| balancePtr | struct IStructs.StoredBalance | storage pointer to balance. |
| amount     | uint256                       | to mint.                    |

### \_increaseNextBalance

```solidity
function _increaseNextBalance(struct IStructs.StoredBalance balancePtr, uint256 amount) internal
```

_Increments the `next` field (but not the `current` field)._

#### Parameters

| Name       | Type                          | Description                 |
| ---------- | ----------------------------- | --------------------------- |
| balancePtr | struct IStructs.StoredBalance | storage pointer to balance. |
| amount     | uint256                       | to increment by.            |

### \_decreaseNextBalance

```solidity
function _decreaseNextBalance(struct IStructs.StoredBalance balancePtr, uint256 amount) internal
```

_Decrements the `next` field (but not the `current` field)._

#### Parameters

| Name       | Type                          | Description                 |
| ---------- | ----------------------------- | --------------------------- |
| balancePtr | struct IStructs.StoredBalance | storage pointer to balance. |
| amount     | uint256                       | to decrement by.            |

### \_storeBalance

```solidity
function _storeBalance(struct IStructs.StoredBalance balancePtr, struct IStructs.StoredBalance balance) private
```

_Stores a balance in storage._

#### Parameters

| Name       | Type                          | Description                               |
| ---------- | ----------------------------- | ----------------------------------------- |
| balancePtr | struct IStructs.StoredBalance | points to where `balance` will be stored. |
| balance    | struct IStructs.StoredBalance | to save to storage.                       |

### \_arePointersEqual

```solidity
function _arePointersEqual(struct IStructs.StoredBalance balancePtrA, struct IStructs.StoredBalance balancePtrB) private pure returns (bool areEqual)
```

_Returns true iff storage pointers resolve to same storage location._

#### Parameters

| Name        | Type                          | Description             |
| ----------- | ----------------------------- | ----------------------- |
| balancePtrA | struct IStructs.StoredBalance | first storage pointer.  |
| balancePtrB | struct IStructs.StoredBalance | second storage pointer. |

#### Return Values

| Name     | Type | Description                  |
| -------- | ---- | ---------------------------- |
| areEqual | bool | true iff pointers are equal. |

## MixinCumulativeRewards

### \_isCumulativeRewardSet

```solidity
function _isCumulativeRewardSet(struct IStructs.Fraction cumulativeReward) internal pure returns (bool)
```

_returns true iff Cumulative Rewards are set_

### \_addCumulativeReward

```solidity
function _addCumulativeReward(bytes32 poolId, uint256 reward, uint256 stake) internal
```

_Sets a pool's cumulative delegator rewards for the current epoch, given the rewards earned and stake from the last epoch, which will be summed with the previous cumulative rewards for this pool. If the last cumulative reward epoch is the current epoch, this is a no-op._

#### Parameters

| Name   | Type    | Description                                                     |
| ------ | ------- | --------------------------------------------------------------- |
| poolId | bytes32 | The pool ID.                                                    |
| reward | uint256 | The total reward earned by pool delegators from the last epoch. |
| stake  | uint256 | The total delegated stake in the pool in the last epoch.        |

### \_updateCumulativeReward

```solidity
function _updateCumulativeReward(bytes32 poolId) internal
```

_Sets a pool's cumulative delegator rewards for the current epoch, using the last stored cumulative rewards. If we've already set a CR for this epoch, this is a no-op._

#### Parameters

| Name   | Type    | Description  |
| ------ | ------- | ------------ |
| poolId | bytes32 | The pool ID. |

### \_computeMemberRewardOverInterval

```solidity
function _computeMemberRewardOverInterval(bytes32 poolId, uint256 memberStakeOverInterval, uint256 beginEpoch, uint256 endEpoch) internal view returns (uint256 reward)
```

_Computes a member's reward over a given epoch interval._

#### Parameters

| Name                    | Type    | Description                                          |
| ----------------------- | ------- | ---------------------------------------------------- |
| poolId                  | bytes32 | Uniqud Id of pool.                                   |
| memberStakeOverInterval | uint256 | Stake delegated to pool by member over the interval. |
| beginEpoch              | uint256 | Beginning of interval.                               |
| endEpoch                | uint256 | End of interval.                                     |

#### Return Values

| Name   | Type    | Description                                              |
| ------ | ------- | -------------------------------------------------------- |
| reward | uint256 | Reward accumulated over interval \[beginEpoch, endEpoch] |

### \_getCumulativeRewardAtEpoch

```solidity
function _getCumulativeRewardAtEpoch(bytes32 poolId, uint256 epoch) private view returns (struct IStructs.Fraction cumulativeReward)
```

_Fetch the cumulative reward for a given epoch. If the corresponding CR does not exist in state, then we backtrack to find its value by querying `epoch-1` and then most recent CR._

#### Parameters

| Name   | Type    | Description           |
| ------ | ------- | --------------------- |
| poolId | bytes32 | Unique ID of pool.    |
| epoch  | uint256 | The epoch to find the |

#### Return Values

| Name             | Type                     | Description                                    |
| ---------------- | ------------------------ | ---------------------------------------------- |
| cumulativeReward | struct IStructs.Fraction | The cumulative reward for `poolId` at `epoch`. |

## MixinStakingPool

### onlyStakingPoolOperator

```solidity
modifier onlyStakingPoolOperator(bytes32 poolId)
```

_Asserts that the sender is the operator of the input pool._

#### Parameters

| Name   | Type    | Description                      |
| ------ | ------- | -------------------------------- |
| poolId | bytes32 | Pool sender must be operator of. |

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```

### createStakingPool

```solidity
function createStakingPool(address rigoblockPoolAddress) external returns (bytes32 poolId)
```

Create a new staking pool. The sender will be the staking pal of this pool.

_Note that a staking pal must be payable. When governance updates registry address, pools must be migrated to new registry, or this contract must query from both._

#### Parameters

| Name                 | Type    | Description                                                                  |
| -------------------- | ------- | ---------------------------------------------------------------------------- |
| rigoblockPoolAddress | address | Adds rigoblock pool to the created staking pool for convenience if non-null. |

#### Return Values

| Name   | Type    | Description                                 |
| ------ | ------- | ------------------------------------------- |
| poolId | bytes32 | The unique pool id generated for this pool. |

### setStakingPalAddress

```solidity
function setStakingPalAddress(bytes32 poolId, address newStakingPalAddress) external
```

Allows the operator to update the staking pal address.

#### Parameters

| Name                 | Type    | Description                     |
| -------------------- | ------- | ------------------------------- |
| poolId               | bytes32 | Unique id of pool.              |
| newStakingPalAddress | address | Address of the new staking pal. |

### decreaseStakingPoolOperatorShare

```solidity
function decreaseStakingPoolOperatorShare(bytes32 poolId, uint32 newOperatorShare) external
```

Decreases the operator share for the given pool (i.e. increases pool rewards for members).

#### Parameters

| Name             | Type    | Description                                                          |
| ---------------- | ------- | -------------------------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                                   |
| newOperatorShare | uint32  | The newly decreased percentage of any rewards owned by the operator. |

### getStakingPool

```solidity
function getStakingPool(bytes32 poolId) public view returns (struct IStructs.Pool)
```

Returns a staking pool

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### \_joinStakingPoolAsRbPoolAccount

```solidity
function _joinStakingPoolAsRbPoolAccount(bytes32 _poold, address _rigoblockPoolAccount) internal
```

_Allows caller to join a staking pool as a rigoblock pool account._

#### Parameters

| Name                   | Type    | Description                                  |
| ---------------------- | ------- | -------------------------------------------- |
| \_poold                | bytes32 | Id of the pool.                              |
| \_rigoblockPoolAccount | address | Address of pool to be added to staking pool. |

### \_assertStakingPoolExists

```solidity
function _assertStakingPoolExists(bytes32 poolId) internal view
```

_Reverts iff a staking pool does not exist._

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### \_assertStakingPoolDoesNotExist

```solidity
function _assertStakingPoolDoesNotExist(bytes32 poolId) internal view
```

_Reverts iff a staking pool does exist._

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### \_assertSenderIsPoolOperator

```solidity
function _assertSenderIsPoolOperator(bytes32 poolId) private view
```

_Asserts that the sender is the operator of the input pool._

#### Parameters

| Name   | Type    | Description                      |
| ------ | ------- | -------------------------------- |
| poolId | bytes32 | Pool sender must be operator of. |

### \_assertDelegateCall

```solidity
function _assertDelegateCall() private view
```

_Preventing direct calls to this contract where applied._

### \_assertNewOperatorShare

```solidity
function _assertNewOperatorShare(uint32 currentOperatorShare, uint32 newOperatorShare) private pure
```

_Reverts iff the new operator share is invalid._

#### Parameters

| Name                 | Type   | Description             |
| -------------------- | ------ | ----------------------- |
| currentOperatorShare | uint32 | Current operator share. |
| newOperatorShare     | uint32 | New operator share.     |

## MixinStakingPoolRewards

### withdrawDelegatorRewards

```solidity
function withdrawDelegatorRewards(bytes32 poolId) external
```

Withdraws the caller's GRG rewards that have accumulated until the last epoch.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

### computeRewardBalanceOfOperator

```solidity
function computeRewardBalanceOfOperator(bytes32 poolId) external view returns (uint256 reward)
```

Computes the reward balance in GRG of the operator of a pool.

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |

#### Return Values

| Name   | Type    | Description     |
| ------ | ------- | --------------- |
| reward | uint256 | Balance in GRG. |

### computeRewardBalanceOfDelegator

```solidity
function computeRewardBalanceOfDelegator(bytes32 poolId, address member) external view returns (uint256 reward)
```

Computes the reward balance in GRG of a specific member of a pool.

#### Parameters

| Name   | Type    | Description             |
| ------ | ------- | ----------------------- |
| poolId | bytes32 | Unique id of pool.      |
| member | address | The member of the pool. |

#### Return Values

| Name   | Type    | Description     |
| ------ | ------- | --------------- |
| reward | uint256 | Balance in GRG. |

### \_withdrawAndSyncDelegatorRewards

```solidity
function _withdrawAndSyncDelegatorRewards(bytes32 poolId, address member) internal
```

_Syncs rewards for a delegator. This includes withdrawing rewards rewards and adding/removing dependencies on cumulative rewards._

#### Parameters

| Name   | Type    | Description        |
| ------ | ------- | ------------------ |
| poolId | bytes32 | Unique id of pool. |
| member | address | of the pool.       |

### \_syncPoolRewards

```solidity
function _syncPoolRewards(bytes32 poolId, uint256 reward, uint256 membersStake) internal returns (uint256 operatorReward, uint256 membersReward)
```

_Handles a pool's reward at the current epoch. This will split the reward between the operator and members, depositing them into their respective vaults, and update the accounting needed to allow members to withdraw their individual rewards._

#### Parameters

| Name         | Type    | Description                                                            |
| ------------ | ------- | ---------------------------------------------------------------------- |
| poolId       | bytes32 | Unique Id of pool.                                                     |
| reward       | uint256 | received by the pool.                                                  |
| membersStake | uint256 | the amount of non-operator delegated stake that will split the reward. |

#### Return Values

| Name           | Type    | Description                                     |
| -------------- | ------- | ----------------------------------------------- |
| operatorReward | uint256 | Portion of `reward` given to the pool operator. |
| membersReward  | uint256 | Portion of `reward` given to the pool members.  |

### \_computePoolRewardsSplit

```solidity
function _computePoolRewardsSplit(uint32 operatorShare, uint256 totalReward, uint256 membersStake) internal pure returns (uint256 operatorReward, uint256 membersReward)
```

_Compute the split of a pool reward between the operator and members based on the `operatorShare` and `membersStake`._

#### Parameters

| Name          | Type    | Description                                                                                           |
| ------------- | ------- | ----------------------------------------------------------------------------------------------------- |
| operatorShare | uint32  | The fraction of rewards owed to the operator, in PPM.                                                 |
| totalReward   | uint256 | The pool reward.                                                                                      |
| membersStake  | uint256 | The amount of member (non-operator) stake delegated to the pool in the epoch the rewards were earned. |

#### Return Values

| Name           | Type    | Description                                          |
| -------------- | ------- | ---------------------------------------------------- |
| operatorReward | uint256 | Portion of `totalReward` given to the pool operator. |
| membersReward  | uint256 | Portion of `totalReward` given to the pool members.  |

### \_computeDelegatorReward

```solidity
function _computeDelegatorReward(bytes32 poolId, address member, uint256 unfinalizedMembersReward, uint256 unfinalizedMembersStake) private view returns (uint256 reward)
```

_Computes the reward balance in ETH of a specific member of a pool._

#### Parameters

| Name                     | Type    | Description                                |
| ------------------------ | ------- | ------------------------------------------ |
| poolId                   | bytes32 | Unique id of pool.                         |
| member                   | address | of the pool.                               |
| unfinalizedMembersReward | uint256 | Unfinalized total members reward (if any). |
| unfinalizedMembersStake  | uint256 | Unfinalized total members stake (if any).  |

#### Return Values

| Name   | Type    | Description      |
| ------ | ------- | ---------------- |
| reward | uint256 | Balance in WETH. |

### \_computeUnfinalizedDelegatorReward

```solidity
function _computeUnfinalizedDelegatorReward(struct IStructs.StoredBalance delegatedStake, uint256 currentEpoch_, uint256 unfinalizedMembersReward, uint256 unfinalizedMembersStake) private pure returns (uint256)
```

_Computes the unfinalized rewards earned by a delegator in the last epoch._

#### Parameters

| Name                     | Type                          | Description                                            |
| ------------------------ | ----------------------------- | ------------------------------------------------------ |
| delegatedStake           | struct IStructs.StoredBalance | Amount of stake delegated to pool by a specific staker |
| currentEpoch\_           | uint256                       | The epoch in which this call is executing              |
| unfinalizedMembersReward | uint256                       | Unfinalized total members reward (if any).             |
| unfinalizedMembersStake  | uint256                       | Unfinalized total members stake (if any).              |

#### Return Values

| Name | Type    | Description             |
| ---- | ------- | ----------------------- |
| \[0] | uint256 | reward Balance in WETH. |

### \_increasePoolRewards

```solidity
function _increasePoolRewards(bytes32 poolId, uint256 amount) private
```

_Increases rewards for a pool._

#### Parameters

| Name   | Type    | Description                     |
| ------ | ------- | ------------------------------- |
| poolId | bytes32 | Unique id of pool.              |
| amount | uint256 | Amount to increment rewards by. |

### \_decreasePoolRewards

```solidity
function _decreasePoolRewards(bytes32 poolId, uint256 amount) private
```

_Decreases rewards for a pool._

#### Parameters

| Name   | Type    | Description                     |
| ------ | ------- | ------------------------------- |
| poolId | bytes32 | Unique id of pool.              |
| amount | uint256 | Amount to decrement rewards by. |

## MixinAbstract

_Exposes some internal functions from various contracts to avoid cyclical dependencies._

### \_getUnfinalizedPoolRewards

```solidity
function _getUnfinalizedPoolRewards(bytes32 poolId) internal view virtual returns (uint256 totalReward, uint256 membersStake)
```

_Computes the reward owed to a pool during finalization. Does nothing if the pool is already finalized._

#### Parameters

| Name   | Type    | Description    |
| ------ | ------- | -------------- |
| poolId | bytes32 | The pool's ID. |

#### Return Values

| Name         | Type    | Description                                                |
| ------------ | ------- | ---------------------------------------------------------- |
| totalReward  | uint256 | The total reward owed to a pool.                           |
| membersStake | uint256 | The total stake for all non-operator members in this pool. |

### \_assertPoolFinalizedLastEpoch

```solidity
function _assertPoolFinalizedLastEpoch(bytes32 poolId) internal view virtual
```

_Asserts that a pool has been finalized last epoch._

#### Parameters

| Name   | Type    | Description                                         |
| ------ | ------- | --------------------------------------------------- |
| poolId | bytes32 | The id of the pool that should have been finalized. |

## MixinFinalizer

### endEpoch

```solidity
function endEpoch() external returns (uint256 numPoolsToFinalize)
```

Begins a new epoch, preparing the prior one for finalization.

_Throws if not enough time has passed between epochs or if the previous epoch was not fully finalized._

#### Return Values

| Name               | Type    | Description                      |
| ------------------ | ------- | -------------------------------- |
| numPoolsToFinalize | uint256 | The number of unfinalized pools. |

### finalizePool

```solidity
function finalizePool(bytes32 poolId) external
```

Instantly finalizes a single pool that earned rewards in the previous epoch,

_crediting it rewards for members and withdrawing operator's rewards as GRG. This can be called by internal functions that need to finalize a pool immediately. Does nothing if the pool is already finalized or did not earn rewards in the previous epoch._

#### Parameters

| Name   | Type    | Description              |
| ------ | ------- | ------------------------ |
| poolId | bytes32 | The pool ID to finalize. |

### \_getUnfinalizedPoolRewards

```solidity
function _getUnfinalizedPoolRewards(bytes32 poolId) internal view virtual returns (uint256 reward, uint256 membersStake)
```

_Computes the reward owed to a pool during finalization. Does nothing if the pool is already finalized._

#### Parameters

| Name   | Type    | Description    |
| ------ | ------- | -------------- |
| poolId | bytes32 | The pool's ID. |

#### Return Values

| Name         | Type    | Description                                                |
| ------------ | ------- | ---------------------------------------------------------- |
| reward       | uint256 | The total reward owed to a pool.                           |
| membersStake | uint256 | The total stake for all non-operator members in this pool. |

### \_getAvailableGrgBalance

```solidity
function _getAvailableGrgBalance() internal view returns (uint256 grgBalance)
```

_Returns the GRG balance of this contract, minus any GRG that has already been reserved for rewards._

### \_assertPoolFinalizedLastEpoch

```solidity
function _assertPoolFinalizedLastEpoch(bytes32 poolId) internal view virtual
```

_Asserts that a pool has been finalized last epoch._

#### Parameters

| Name   | Type    | Description                                         |
| ------ | ------- | --------------------------------------------------- |
| poolId | bytes32 | The id of the pool that should have been finalized. |

### \_getUnfinalizedPoolRewardsFromPoolStats

```solidity
function _getUnfinalizedPoolRewardsFromPoolStats(struct IStructs.PoolStats poolStats, struct IStructs.AggregatedStats aggregatedStats) private view returns (uint256 rewards)
```

_Computes the reward owed to a pool during finalization._

#### Parameters

| Name            | Type                            | Description                        |
| --------------- | ------------------------------- | ---------------------------------- |
| poolStats       | struct IStructs.PoolStats       | Stats for a specific pool.         |
| aggregatedStats | struct IStructs.AggregatedStats | Stats aggregated across all pools. |

#### Return Values

| Name    | Type    | Description                             |
| ------- | ------- | --------------------------------------- |
| rewards | uint256 | Unfinalized rewards for the input pool. |

## MixinParams

### setParams

```solidity
function setParams(uint256 _epochDurationInSeconds, uint32 _rewardDelegatedStakeWeight, uint256 _minimumPoolStake, uint32 _cobbDouglasAlphaNumerator, uint32 _cobbDouglasAlphaDenominator) external
```

Set all configurable parameters at once.

#### Parameters

| Name                          | Type    | Description                                                     |
| ----------------------------- | ------- | --------------------------------------------------------------- |
| \_epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| \_rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| \_minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| \_cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                        |
| \_cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                      |

### getParams

```solidity
function getParams() external view returns (uint256 _epochDurationInSeconds, uint32 _rewardDelegatedStakeWeight, uint256 _minimumPoolStake, uint32 _cobbDouglasAlphaNumerator, uint32 _cobbDouglasAlphaDenominator)
```

_Retrieves all configurable parameter values._

#### Return Values

| Name                          | Type    | Description                                                     |
| ----------------------------- | ------- | --------------------------------------------------------------- |
| \_epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| \_rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| \_minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| \_cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                        |
| \_cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                      |

### \_initMixinParams

```solidity
function _initMixinParams() internal
```

_Initialize storage belonging to this mixin._

### \_assertParamsNotInitialized

```solidity
function _assertParamsNotInitialized() internal view
```

_Asserts that upgradable storage has not yet been initialized._

### \_setParams

```solidity
function _setParams(uint256 _epochDurationInSeconds, uint32 _rewardDelegatedStakeWeight, uint256 _minimumPoolStake, uint32 _cobbDouglasAlphaNumerator, uint32 _cobbDouglasAlphaDenominator) private
```

_Set all configurable parameters at once._

#### Parameters

| Name                          | Type    | Description                                                     |
| ----------------------------- | ------- | --------------------------------------------------------------- |
| \_epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                 |
| \_rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm. |
| \_minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.  |
| \_cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                        |
| \_cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                      |

## MixinScheduler

### getCurrentEpochEarliestEndTimeInSeconds

```solidity
function getCurrentEpochEarliestEndTimeInSeconds() public view returns (uint256)
```

Returns the earliest end time in seconds of this epoch.

_The next epoch can begin once this time is reached. Epoch period = \[startTimeInSeconds..endTimeInSeconds)_

#### Return Values

| Name | Type    | Description      |
| ---- | ------- | ---------------- |
| \[0] | uint256 | Time in seconds. |

### \_initMixinScheduler

```solidity
function _initMixinScheduler() internal
```

_Initializes state owned by this mixin. Fails if state was already initialized._

### \_goToNextEpoch

```solidity
function _goToNextEpoch() internal
```

_Moves to the next epoch, given the current epoch period has ended. Time intervals that are measured in epochs (like timeLocks) are also incremented, given their periods have ended._

### \_assertSchedulerNotInitialized

```solidity
function _assertSchedulerNotInitialized() internal view
```

_Assert scheduler state before initializing it. This must be updated for each migration._
