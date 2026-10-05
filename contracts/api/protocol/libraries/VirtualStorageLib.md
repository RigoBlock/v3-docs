# VirtualStorageLib

## Overview

#### License: Apache-2.0-or-later

```solidity
library VirtualStorageLib
```

Provides functions to get and update virtual supply (VS-only model)

Uses ERC-7201 namespaced storage pattern

VS-only model: Transfer writes negative VS on source (NAV-neutral), positive VS on destination
Sync has no VS impact (NAV-impacting on both chains)
## Structs info

### VirtualSupply

```solidity
struct VirtualSupply {
	int256 supply;
}
```


## Constants info

### VIRTUAL_SUPPLY_SLOT (0xfb5203b7)

```solidity
bytes32 constant VIRTUAL_SUPPLY_SLOT = 0xc1634c3ed93b1f7aa4d725c710ac3b239c1d30894404e630b60009ee3411450f
```


## Functions info

### virtualSupply

```solidity
function virtualSupply()
    internal
    pure
    returns (VirtualStorageLib.VirtualSupply storage s)
```


### updateVirtualSupply

```solidity
function updateVirtualSupply(int256 delta) internal
```


### getVirtualSupply

```solidity
function getVirtualSupply() internal view returns (int256)
```

