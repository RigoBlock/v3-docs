# EUpgrade

## Overview

#### License: Apache 2.0

```solidity
contract EUpgrade is IEUpgrade
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Errors info

### EUpgradeDirectCall

```solidity
error EUpgradeDirectCall()
```


### EUpgradeImplementationIsSameAsCurrent

```solidity
error EUpgradeImplementationIsSameAsCurrent()
```


## Functions info

### constructor

```solidity
constructor(address factory)
```


### upgradeImplementation (0x466f3dc3)

```solidity
function upgradeImplementation() external override
```

Allows caller to upgrade pool implementation.

Cannot be called directly and in pool is restricted to pool owner.
### getBeacon (0x2d6b3a6b)

```solidity
function getBeacon() public view override returns (address)
```

Returns the implementation beacon.
Address of the beacon.