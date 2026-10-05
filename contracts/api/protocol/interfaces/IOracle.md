# IOracle

## Overview

#### License: GPL-2.0-or-later

```solidity
interface IOracle
```


## Structs info

### ObservationState

```solidity
struct ObservationState {
	uint16 index;
	uint16 cardinality;
	uint16 cardinalityNext;
}
```

index: The index of the last written observation for the pool

cardinality: The cardinality of the observations array for the pool
@custom:cardinalityNext The cardinality target of the observations array for the pool, which will replace cardinality when enough observations are written
## Functions info

### increaseCardinalityNext (0x8f1c9217)

```solidity
function increaseCardinalityNext(
    PoolKey calldata key,
    uint16 cardinalityNext
) external returns (uint16 cardinalityNextOld, uint16 cardinalityNextNew)
```


### getObservation (0xefb40e57)

```solidity
function getObservation(
    PoolKey calldata key,
    uint256 index
) external view returns (Observation memory observation)
```


### getState (0xe3b077a1)

```solidity
function getState(
    PoolKey calldata key
) external view returns (IOracle.ObservationState memory state)
```


### observe (0xf96f97f2)

```solidity
function observe(
    PoolKey calldata key,
    uint32[] calldata secondsAgos
)
    external
    view
    returns (
        int48[] memory tickCumulatives,
        uint144[] memory secondsPerLiquidityCumulativeX128s
    )
```

