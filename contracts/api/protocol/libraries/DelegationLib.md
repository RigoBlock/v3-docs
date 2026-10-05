# DelegationLib

## Overview

#### License: Apache 2.0

```solidity
library DelegationLib
```

Library for managing granular per-selector delegated write access to pool adapters.

All writes maintain two enumerable index structures so callers can enumerate delegations
in either direction without iterating unpredictably large arrays.
## Functions info

### add

```solidity
function add(
    DelegationData storage self,
    bytes4 selector,
    address addr
) internal returns (bool added)
```

Grants delegated write access to `selector` for `addr`.


Return values:

| Name  | Type | Description                                                                      |
| :---- | :--- | :------------------------------------------------------------------------------- |
| added | bool | True if the pair was newly granted (false = already existed, no storage change). |

### remove

```solidity
function remove(
    DelegationData storage self,
    bytes4 selector,
    address addr
) internal returns (bool removed)
```

Revokes delegated write access to `selector` for `addr`.


Return values:

| Name    | Type | Description                                                                              |
| :------ | :--- | :--------------------------------------------------------------------------------------- |
| removed | bool | True if the pair was present and removed (false = was not delegated, no storage change). |

### removeAllByAddress

```solidity
function removeAllByAddress(DelegationData storage self, address addr) internal
```

Revokes all delegations previously granted to `addr` (e.g. compromised wallet).

Iterates the (short) list of selectors for addr and cleans up both directions.
### removeAllBySelector

```solidity
function removeAllBySelector(
    DelegationData storage self,
    bytes4 selector
) internal
```

Revokes all delegations for `selector` (e.g. adapter being replaced by governance).

Iterates the (short) list of addresses for selector and cleans up both directions.
### getAddresses

```solidity
function getAddresses(
    DelegationData storage self,
    bytes4 selector
) internal view returns (address[] memory)
```

Returns all addresses currently delegated for `selector`.
### getSelectors

```solidity
function getSelectors(
    DelegationData storage self,
    address addr
) internal view returns (bytes4[] memory)
```

Returns all selectors currently delegated to `addr`.