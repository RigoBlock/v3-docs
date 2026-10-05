# MixinParams

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinParams is IStaking, IStakingEvents, MixinStorage, MixinConstants
```


## Functions info

### setParams (0x9c3ccc82)

```solidity
function setParams(
    uint256 _epochDurationInSeconds,
    uint32 _rewardDelegatedStakeWeight,
    uint256 _minimumPoolStake,
    uint32 _cobbDouglasAlphaNumerator,
    uint32 _cobbDouglasAlphaDenominator
) external override onlyAuthorized
```

Set all configurable parameters at once.


Parameters:

| Name                         | Type    | Description                                                      |
| :--------------------------- | :------ | :--------------------------------------------------------------- |
| _epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                  |
| _rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm.  |
| _minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.   |
| _cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                         |
| _cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                       |

### getParams (0x5e615a6b)

```solidity
function getParams()
    external
    view
    override
    returns (
        uint256 _epochDurationInSeconds,
        uint32 _rewardDelegatedStakeWeight,
        uint256 _minimumPoolStake,
        uint32 _cobbDouglasAlphaNumerator,
        uint32 _cobbDouglasAlphaDenominator
    )
```

Retrieves all configurable parameter values.


Return values:

| Name                         | Type    | Description                                                      |
| :--------------------------- | :------ | :--------------------------------------------------------------- |
| _epochDurationInSeconds      | uint256 | Minimum seconds between epochs.                                  |
| _rewardDelegatedStakeWeight  | uint32  | How much delegated stake is weighted vs operator stake, in ppm.  |
| _minimumPoolStake            | uint256 | Minimum amount of stake required in a pool to collect rewards.   |
| _cobbDouglasAlphaNumerator   | uint32  | Numerator for cobb douglas alpha factor.                         |
| _cobbDouglasAlphaDenominator | uint32  | Denominator for cobb douglas alpha factor.                       |
