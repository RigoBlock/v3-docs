# MixinScheduler

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinScheduler is IStaking, IStakingEvents, MixinStorage
```


## Functions info

### getCurrentEpochEarliestEndTimeInSeconds (0xb2baa33e)

```solidity
function getCurrentEpochEarliestEndTimeInSeconds()
    public
    view
    override
    returns (uint256)
```

Returns the earliest end time in seconds of this epoch.

The next epoch can begin once this time is reached.

Epoch period = [startTimeInSeconds..endTimeInSeconds)


Return values:

| Name | Type    | Description      |
| :--- | :------ | :--------------- |
| [0]  | uint256 | Time in seconds. |
