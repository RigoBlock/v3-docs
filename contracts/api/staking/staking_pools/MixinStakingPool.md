# MixinStakingPool

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinStakingPool is MixinStakingPoolRewards
```


## Modifiers info

### onlyStakingPoolOperator

```solidity
modifier onlyStakingPoolOperator(bytes32 poolId)
```

Asserts that the sender is the operator of the input pool.


Parameters:

| Name   | Type    | Description                      |
| :----- | :------ | :------------------------------- |
| poolId | bytes32 | Pool sender must be operator of. |

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### createStakingPool (0xbe111af4)

```solidity
function createStakingPool(
    address rigoblockPoolAddress
) external override onlyDelegateCall returns (bytes32 poolId)
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
) external override onlyStakingPoolOperator(poolId)
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
) external override onlyStakingPoolOperator(poolId)
```

Decreases the operator share for the given pool (i.e. increases pool rewards for members).


Parameters:

| Name             | Type    | Description                                                          |
| :--------------- | :------ | :------------------------------------------------------------------- |
| poolId           | bytes32 | Unique Id of pool.                                                   |
| newOperatorShare | uint32  | The newly decreased percentage of any rewards owned by the operator. |

### getStakingPool (0x4bcc3f67)

```solidity
function getStakingPool(
    bytes32 poolId
) public view override returns (IStructs.Pool memory)
```

Returns a staking pool


Parameters:

| Name   | Type    | Description        |
| :----- | :------ | :----------------- |
| poolId | bytes32 | Unique id of pool. |
