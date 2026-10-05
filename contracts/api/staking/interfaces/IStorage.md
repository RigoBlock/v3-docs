# IStorage

## Overview

#### License: Apache 2.0

```solidity
interface IStorage
```


## Functions info

### stakingContract (0xee99205c)

```solidity
function stakingContract() external view returns (address)
```

Address of staking contract.


Return values:

| Name | Type    | Description                                      |
| :--- | :------ | :----------------------------------------------- |
| [0]  | address | stakingContract Address of the staking contract. |

### poolIdByRbPoolAccount (0x7fa140c7)

```solidity
function poolIdByRbPoolAccount(address) external view returns (bytes32)
```

Mapping from RigoBlock pool subaccount to pool Id of rigoblock pool

0 RigoBlock pool subaccount address.


Return values:

| Name | Type    | Description    |
| :--- | :------ | :------------- |
| [0]  | bytes32 | 0 The pool ID. |

### rewardsByPoolId (0xc18c9141)

```solidity
function rewardsByPoolId(bytes32) external view returns (uint256)
```

mapping from pool ID to reward balance of members

0 Pool ID.


Return values:

| Name | Type    | Description                                         |
| :--- | :------ | :-------------------------------------------------- |
| [0]  | uint256 | 0 The total reward balance of members in this pool. |

### currentEpoch (0x76671808)

```solidity
function currentEpoch() external view returns (uint256)
```

The current epoch.


Return values:

| Name | Type    | Description                                   |
| :--- | :------ | :-------------------------------------------- |
| [0]  | uint256 | currentEpoch The number of the current epoch. |

### currentEpochStartTimeInSeconds (0x587da023)

```solidity
function currentEpochStartTimeInSeconds() external view returns (uint256)
```

The current epoch start time.


Return values:

| Name | Type    | Description                                             |
| :--- | :------ | :------------------------------------------------------ |
| [0]  | uint256 | currentEpochStartTimeInSeconds Timestamp of start time. |

### validPops (0x540c2d53)

```solidity
function validPops(address popAddress) external view returns (bool)
```

Registered RigoBlock Proof_of_Performance contracts, capable of paying protocol fees.

0 The address to check.


Return values:

| Name | Type | Description                                                 |
| :--- | :--- | :---------------------------------------------------------- |
| [0]  | bool | 0 Whether the address is a registered proof_of_performance. |

### epochDurationInSeconds (0x63403801)

```solidity
function epochDurationInSeconds() external view returns (uint256)
```

Minimum seconds between epochs.


Return values:

| Name | Type    | Description                               |
| :--- | :------ | :---------------------------------------- |
| [0]  | uint256 | epochDurationInSeconds Number of seconds. |

### rewardDelegatedStakeWeight (0xe0ee036e)

```solidity
function rewardDelegatedStakeWeight() external view returns (uint32)
```



Return values:

| Name | Type   | Description                                              |
| :--- | :----- | :------------------------------------------------------- |
| [0]  | uint32 | rewardDelegatedStakeWeight Number in units of a million. |

### minimumPoolStake (0xa26171e2)

```solidity
function minimumPoolStake() external view returns (uint256)
```

Minimum amount of stake required in a pool to collect rewards.


Return values:

| Name | Type    | Description                               |
| :--- | :------ | :---------------------------------------- |
| [0]  | uint256 | minimumPoolStake Minimum amount required. |

### cobbDouglasAlphaNumerator (0x81666796)

```solidity
function cobbDouglasAlphaNumerator() external view returns (uint32)
```

Numerator for cobb douglas alpha factor.


Return values:

| Name | Type   | Description                                        |
| :--- | :----- | :------------------------------------------------- |
| [0]  | uint32 | cobbDouglasAlphaNumerator Number of the numerator. |

### cobbDouglasAlphaDenominator (0xe8eeb3f8)

```solidity
function cobbDouglasAlphaDenominator() external view returns (uint32)
```

Denominator for cobb douglas alpha factor.


Return values:

| Name | Type   | Description                                            |
| :--- | :----- | :----------------------------------------------------- |
| [0]  | uint32 | cobbDouglasAlphaDenominator Number of the denominator. |

### poolStatsByEpoch (0x2a94c279)

```solidity
function poolStatsByEpoch(
    bytes32 key,
    uint256 epoch
)
    external
    view
    returns (
        uint256 feesCollected,
        uint256 weightedStake,
        uint256 membersStake
    )
```

Stats for each pool that generated fees with sufficient stake to earn rewards.

See `_minimumPoolStake` in `MixinParams`.


Parameters:

| Name  | Type    | Description    |
| :---- | :------ | :------------- |
| key   | bytes32 | Pool ID.       |
| epoch | uint256 | Epoch number.  |


Return values:

| Name          | Type    | Description                         |
| :------------ | :------ | :---------------------------------- |
| feesCollected | uint256 | Amount of fees collected in epoch.  |
| weightedStake | uint256 | Weighted stake per million.         |
| membersStake  | uint256 | Members stake per million.          |

### aggregatedStatsByEpoch (0x38229d93)

```solidity
function aggregatedStatsByEpoch(
    uint256 epoch
)
    external
    view
    returns (
        uint256 rewardsAvailable,
        uint256 numPoolsToFinalize,
        uint256 totalFeesCollected,
        uint256 totalWeightedStake,
        uint256 totalRewardsFinalized
    )
```

Aggregated stats across all pools that generated fees with sufficient stake to earn rewards.

See `_minimumPoolStake` in MixinParams.


Parameters:

| Name  | Type    | Description    |
| :---- | :------ | :------------- |
| epoch | uint256 | Epoch number.  |


Return values:

| Name                  | Type    | Description                                                                   |
| :-------------------- | :------ | :---------------------------------------------------------------------------- |
| rewardsAvailable      | uint256 | Rewards (GRG) available to the epoch being finalized (the previous epoch).    |
| numPoolsToFinalize    | uint256 | The number of pools that have yet to be finalized through `finalizePools()`.  |
| totalFeesCollected    | uint256 | The total fees collected for the epoch being finalized.                       |
| totalWeightedStake    | uint256 | The total fees collected for the epoch being finalized.                       |
| totalRewardsFinalized | uint256 | Amount of rewards that have been paid during finalization.                    |

### grgReservedForPoolRewards (0xd14dc231)

```solidity
function grgReservedForPoolRewards() external view returns (uint256)
```

The GRG balance of this contract that is reserved for pool reward payouts.


Return values:

| Name | Type    | Description                                                      |
| :--- | :------ | :--------------------------------------------------------------- |
| [0]  | uint256 | grgReservedForPoolRewards Number of tokens reserved for rewards. |
