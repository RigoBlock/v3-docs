# MixinStorage

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinStorage is IStorage, Authorizable
```


## State variables info

### stakingContract (0xee99205c)

```solidity
address stakingContract
```


### poolIdByRbPoolAccount (0x7fa140c7)

```solidity
mapping(address => bytes32) poolIdByRbPoolAccount
```


### rewardsByPoolId (0xc18c9141)

```solidity
mapping(bytes32 => uint256) rewardsByPoolId
```


### currentEpoch (0x76671808)

```solidity
uint256 currentEpoch
```


### currentEpochStartTimeInSeconds (0x587da023)

```solidity
uint256 currentEpochStartTimeInSeconds
```


### validPops (0x540c2d53)

```solidity
mapping(address => bool) validPops
```


### epochDurationInSeconds (0x63403801)

```solidity
uint256 epochDurationInSeconds
```


### rewardDelegatedStakeWeight (0xe0ee036e)

```solidity
uint32 rewardDelegatedStakeWeight
```


### minimumPoolStake (0xa26171e2)

```solidity
uint256 minimumPoolStake
```


### cobbDouglasAlphaNumerator (0x81666796)

```solidity
uint32 cobbDouglasAlphaNumerator
```


### cobbDouglasAlphaDenominator (0xe8eeb3f8)

```solidity
uint32 cobbDouglasAlphaDenominator
```


### poolStatsByEpoch (0x2a94c279)

```solidity
mapping(bytes32 => mapping(uint256 => struct IStructs.PoolStats)) poolStatsByEpoch
```


### aggregatedStatsByEpoch (0x38229d93)

```solidity
mapping(uint256 => struct IStructs.AggregatedStats) aggregatedStatsByEpoch
```


### grgReservedForPoolRewards (0xd14dc231)

```solidity
uint256 grgReservedForPoolRewards
```

