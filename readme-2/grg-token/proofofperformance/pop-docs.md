# Solidity API

## ProofOfPerformance

### \_stakingProxy

```solidity
address _stakingProxy
```

### constructor

```solidity
constructor(address stakingProxy) public
```

### creditPopRewardToStakingProxy

```solidity
function creditPopRewardToStakingProxy(address targetPool) external
```

_Credits the pop reward to the Staking Proxy contract._

#### Parameters

| Name       | Type    | Description          |
| ---------- | ------- | -------------------- |
| targetPool | address | Address of the pool. |

### proofOfPerformance

```solidity
function proofOfPerformance(address targetPool) external view returns (uint256)
```

_Returns the proof of performance reward for a pool._

#### Parameters

| Name       | Type    | Description          |
| ---------- | ------- | -------------------- |
| targetPool | address | Address of the pool. |

#### Return Values

| Name | Type    | Description                             |
| ---- | ------- | --------------------------------------- |
| \[0] | uint256 | Value of the pop reward in Rigo tokens. |

### \_getStakingProxy

```solidity
function _getStakingProxy() private view returns (address)
```
