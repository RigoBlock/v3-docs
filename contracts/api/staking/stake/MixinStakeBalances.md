# MixinStakeBalances

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinStakeBalances is MixinStakeStorage, MixinDeploymentConstants
```


## Functions info

### getGlobalStakeByStatus (0xe804d0a4)

```solidity
function getGlobalStakeByStatus(
    IStructs.StakeStatus stakeStatus
) external view override returns (IStructs.StoredBalance memory balance)
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
) external view override returns (IStructs.StoredBalance memory balance)
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
function getTotalStake(address staker) public view override returns (uint256)
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

### getStakeDelegatedToPoolByOwner (0xf252b7a1)

```solidity
function getStakeDelegatedToPoolByOwner(
    address staker,
    bytes32 poolId
) public view override returns (IStructs.StoredBalance memory balance)
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

### getTotalStakeDelegatedToPool (0x3e4ad732)

```solidity
function getTotalStakeDelegatedToPool(
    bytes32 poolId
) public view override returns (IStructs.StoredBalance memory balance)
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
