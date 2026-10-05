# IAStaking

## Overview

#### License: Apache 2.0

```solidity
interface IAStaking
```


## Functions info

### stake (0xa694fc3a)

```solidity
function stake(uint256 amount) external
```

Stakes an amount of GRG to own staking pool. Creates staking pool if doesn't exist.

Creating staking pool if doesn't exist effectively locks direct call.


Parameters:

| Name   | Type    | Description             |
| :----- | :------ | :---------------------- |
| amount | uint256 | Amount of GRG to stake. |

### undelegateStake (0x4aace835)

```solidity
function undelegateStake(uint256 amount) external
```

Undelegates stake for the pool.


Parameters:

| Name   | Type    | Description                          |
| :----- | :------ | :----------------------------------- |
| amount | uint256 | Number of GRG units with undelegate. |

### unstake (0x2e17de78)

```solidity
function unstake(uint256 amount) external
```

Unstakes staked undelegated tokens for the pool.


Parameters:

| Name   | Type    | Description                     |
| :----- | :------ | :------------------------------ |
| amount | uint256 | Number of GRG units to unstake. |

### withdrawDelegatorRewards (0xb880660b)

```solidity
function withdrawDelegatorRewards() external
```

Withdraws delegator rewards of the pool.