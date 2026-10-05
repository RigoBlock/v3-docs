# EnumerableSet

## Overview

#### License: Apache 2.0

```solidity
library EnumerableSet
```

Adapted from https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/structs/EnumerableSet.sol
## Errors info

### AddressListExceedsMaxLength

```solidity
error AddressListExceedsMaxLength()
```


### TokenPriceFeedDoesNotExist

```solidity
error TokenPriceFeedDoesNotExist(address token)
```


## Functions info

### addUnique

```solidity
function addUnique(
    AddressSet storage set,
    IEOracle eOracle,
    address token,
    address baseToken
) internal returns (bool wasActive)
```

Adds `token` to the set if it is not the base token and not already active.

Reads set.positions[token] exactly once. Returns whether the token was active
before this call (base token is always considered active and is never stored).
### remove

```solidity
function remove(AddressSet storage set, address token) internal
```


### isActive

```solidity
function isActive(
    AddressSet storage set,
    address token
) internal view returns (bool)
```


### add

```solidity
function add(Bytes32Set storage set, bytes32 value) internal
```


### remove

```solidity
function remove(Bytes32Set storage set, bytes32 value) internal
```


### contains

```solidity
function contains(
    Bytes32Set storage set,
    bytes32 value
) internal view returns (bool)
```


### length

```solidity
function length(Bytes32Set storage set) internal view returns (uint256)
```


### at

```solidity
function at(
    Bytes32Set storage set,
    uint256 index
) internal view returns (bytes32)
```

