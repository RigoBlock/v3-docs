# ProofOfPerformance

## Overview

#### License: Apache 2.0

```solidity
contract ProofOfPerformance is IProofOfPerformance
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### constructor

```solidity
constructor(address stakingProxy)
```


### creditPopRewardToStakingProxy (0xd1c7e2fe)

```solidity
function creditPopRewardToStakingProxy(address targetPool) external override
```

Credits the pop reward to the Staking Proxy contract.


Parameters:

| Name       | Type    | Description          |
| :--------- | :------ | :------------------- |
| targetPool | address | Address of the pool. |

### proofOfPerformance (0x18210523)

```solidity
function proofOfPerformance(
    address targetPool
) external view override returns (uint256)
```

Returns the proof of performance reward for a pool.


Parameters:

| Name       | Type    | Description           |
| :--------- | :------ | :-------------------- |
| targetPool | address | Address of the pool.  |


Return values:

| Name | Type    | Description                             |
| :--- | :------ | :-------------------------------------- |
| [0]  | uint256 | Value of the pop reward in Rigo tokens. |
