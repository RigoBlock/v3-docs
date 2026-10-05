# IStructs

## Overview

#### License: Apache 2.0

```solidity
interface IStructs
```


## Enums info

### StakeStatus

```solidity
enum StakeStatus {
	 UNDELEGATED,
	 DELEGATED
}
```

Statuses that stake can exist in.

Any stake can be (re)delegated effective at the next epoch.

Undelegated stake can be withdrawn if it is available in both the current and next epoch.
## Structs info

### PoolStats

```solidity
struct PoolStats {
	uint256 feesCollected;
	uint256 weightedStake;
	uint256 membersStake;
}
```

Stats for a pool that earned rewards.


Parameters:

| Name          | Type    | Description                               |
| :------------ | :------ | :---------------------------------------- |
| feesCollected | uint256 | Fees collected in ETH by this pool.       |
| weightedStake | uint256 | Amount of weighted stake in the pool.     |
| membersStake  | uint256 | Amount of non-operator stake in the pool. |

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

Holds stats aggregated across a set of pools.

rewardsAvailable is simply the balanc of the contract at the end of the epoch.


Parameters:

| Name                  | Type    | Description                                                                   |
| :-------------------- | :------ | :---------------------------------------------------------------------------- |
| rewardsAvailable      | uint256 | Rewards (GRG) available to the epoch being finalized (the previous epoch).    |
| numPoolsToFinalize    | uint256 | The number of pools that have yet to be finalized through `finalizePools()`.  |
| totalFeesCollected    | uint256 | The total fees collected for the epoch being finalized.                       |
| totalWeightedStake    | uint256 | The total fees collected for the epoch being finalized.                       |
| totalRewardsFinalized | uint256 | Amount of rewards that have been paid during finalization.                    |

### StoredBalance

```solidity
struct StoredBalance {
	uint64 currentEpoch;
	uint96 currentEpochBalance;
	uint96 nextEpochBalance;
}
```

Encapsulates a balance for the current and next epochs.

Note that these balances may be stale if the current epoch is greater than `currentEpoch`.


Parameters:

| Name                | Type   | Description                    |
| :------------------ | :----- | :----------------------------- |
| currentEpoch        | uint64 | The current epoch              |
| currentEpochBalance | uint96 | Balance in the current epoch.  |
| nextEpochBalance    | uint96 | Balance in `currentEpoch+1`.   |

### StakeInfo

```solidity
struct StakeInfo {
	IStructs.StakeStatus status;
	bytes32 poolId;
}
```

Info used to describe a status.


Parameters:

| Name   | Type                      | Description                                           |
| :----- | :------------------------ | :---------------------------------------------------- |
| status | enum IStructs.StakeStatus | Status of the stake.                                  |
| poolId | bytes32                   | Unique Id of pool. This is set when status=DELEGATED. |

### Fraction

```solidity
struct Fraction {
	uint256 numerator;
	uint256 denominator;
}
```

Struct to represent a fraction.


Parameters:

| Name        | Type    | Description              |
| :---------- | :------ | :----------------------- |
| numerator   | uint256 | Numerator of fraction.   |
| denominator | uint256 | Denominator of fraction. |

### Pool

```solidity
struct Pool {
	address operator;
	address stakingPal;
	uint32 operatorShare;
	uint32 stakingPalShare;
}
```

Holds the metadata for a staking pool.


Parameters:

| Name            | Type    | Description                                                       |
| :-------------- | :------ | :---------------------------------------------------------------- |
| operator        | address | Operator of the pool.                                             |
| stakingPal      | address | Staking pal of the pool.                                          |
| operatorShare   | uint32  | Fraction of the total balance owned by the operator, in ppm.      |
| stakingPalShare | uint32  | Fraction of the operator reward owned by the staking pal, in ppm. |
