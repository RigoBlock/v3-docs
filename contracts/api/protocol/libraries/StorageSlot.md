# StorageSlot

## Overview

#### License: Apache-2.0-or-later

```solidity
library StorageSlot
```


## Structs info

### AddressSlot

```solidity
struct AddressSlot {
	address value;
}
```


## Functions info

### getAddressSlot

```solidity
function getAddressSlot(
    bytes32 slot
) internal pure returns (StorageSlot.AddressSlot storage r)
```

