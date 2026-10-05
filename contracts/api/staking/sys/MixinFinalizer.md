# MixinFinalizer

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinFinalizer is MixinStakingPoolRewards
```


## Functions info

### endEpoch (0x0b9663db)

```solidity
function endEpoch() external override returns (uint256 numPoolsToFinalize)
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
function finalizePool(bytes32 poolId) external override
```

Instantly finalizes a single pool that earned rewards in the previous epoch,

crediting it rewards for members and withdrawing operator's rewards as GRG.

This can be called by internal functions that need to finalize a pool immediately.

Does nothing if the pool is already finalized or did not earn rewards in the previous epoch.


Parameters:

| Name   | Type    | Description              |
| :----- | :------ | :----------------------- |
| poolId | bytes32 | The pool ID to finalize. |
