# MixinStake

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinStake is MixinStakingPool
```


## Functions info

### stake (0xa694fc3a)

```solidity
function stake(uint256 amount) external override
```

Stake GRG tokens. Tokens are deposited into the GRG Vault.

Unstake to retrieve the GRG. Stake is in the 'Active' status.


Parameters:

| Name   | Type    | Description      |
| :----- | :------ | :--------------- |
| amount | uint256 | of GRG to stake. |

### unstake (0x2e17de78)

```solidity
function unstake(uint256 amount) external override
```

Unstake. Tokens are withdrawn from the GRG Vault and returned to the staker.

Stake must be in the 'undelegated' status in both the current and next epoch in order to be unstaked.


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| amount | uint256 | of GRG to unstake. |

### moveStake (0x58f6c7e3)

```solidity
function moveStake(
    IStructs.StakeInfo calldata from,
    IStructs.StakeInfo calldata to,
    uint256 amount
) external override
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
