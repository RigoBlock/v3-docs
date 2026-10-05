# IEUpgrade

## Overview

#### License: Apache 2.0

```solidity
interface IEUpgrade
```


## Events info

### Upgraded

```solidity
event Upgraded(address indexed implementation)
```

Emitted when pool operator upgrades proxy implementation address.


Parameters:

| Name           | Type    | Description                        |
| :------------- | :------ | :--------------------------------- |
| implementation | address | Address of the new implementation. |

## Functions info

### upgradeImplementation (0x466f3dc3)

```solidity
function upgradeImplementation() external
```

Allows caller to upgrade pool implementation.

Cannot be called directly and in pool is restricted to pool owner.
### getBeacon (0x2d6b3a6b)

```solidity
function getBeacon() external view returns (address)
```

Returns the implementation beacon.
Address of the beacon.