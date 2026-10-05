# AStaking

## Overview

#### License: Apache 2.0

```solidity
contract AStaking is IAStaking
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### constructor

```solidity
constructor(address stakingProxy, address grgToken, address grgTransferProxy)
```


### stake (0xa694fc3a)

```solidity
function stake(uint256 amount) external override
```

Stakes an amount of GRG to own staking pool. Creates staking pool if doesn't exist.

Creating staking pool if doesn't exist effectively locks direct call.


Parameters:

| Name   | Type    | Description             |
| :----- | :------ | :---------------------- |
| amount | uint256 | Amount of GRG to stake. |

### undelegateStake (0x4aace835)

```solidity
function undelegateStake(uint256 amount) external override
```

Undelegates stake for the pool.


Parameters:

| Name   | Type    | Description                          |
| :----- | :------ | :----------------------------------- |
| amount | uint256 | Number of GRG units with undelegate. |

### unstake (0x2e17de78)

```solidity
function unstake(uint256 amount) external override
```

Unstakes staked undelegated tokens for the pool.


Parameters:

| Name   | Type    | Description                     |
| :----- | :------ | :------------------------------ |
| amount | uint256 | Number of GRG units to unstake. |

### withdrawDelegatorRewards (0xb880660b)

```solidity
function withdrawDelegatorRewards() external override
```

Withdraws delegator rewards of the pool.