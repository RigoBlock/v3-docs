# TransientSlot

## Overview

#### License: MIT

```solidity
library TransientSlot
```

Library for reading and writing value-types to specific transient storage slots.

Transient slots are often used to store temporary values that are removed after the current transaction.
This library helps with reading and writing to such slots without the need for inline assembly.

* Example reading and writing values using transient storage:
```solidity
contract Lock {
    using TransientSlot for *;

    // Define the slot. Alternatively, use the SlotDerivation library to derive the slot.
    bytes32 internal constant _LOCK_SLOT = 0xf4678858b2b588224636b8522b729e7722d32fc491da849ed75b3fdf3c84f542;

    modifier locked() {
        require(!_LOCK_SLOT.asBoolean().tload());

        _LOCK_SLOT.asBoolean().tstore(true);
        _;
        _LOCK_SLOT.asBoolean().tstore(false);
    }
}
```

TIP: Consider using this library along with {SlotDerivation}.
## Functions info

### asAddress

```solidity
function asAddress(
    bytes32 slot
) internal pure returns (TransientSlot.AddressSlot)
```

Cast an arbitrary slot to a AddressSlot.
### asBoolean

```solidity
function asBoolean(
    bytes32 slot
) internal pure returns (TransientSlot.BooleanSlot)
```

Cast an arbitrary slot to a BooleanSlot.
### asBytes32

```solidity
function asBytes32(
    bytes32 slot
) internal pure returns (TransientSlot.Bytes32Slot)
```

Cast an arbitrary slot to a Bytes32Slot.
### asUint256

```solidity
function asUint256(
    bytes32 slot
) internal pure returns (TransientSlot.Uint256Slot)
```

Cast an arbitrary slot to a Uint256Slot.
### asInt256

```solidity
function asInt256(
    bytes32 slot
) internal pure returns (TransientSlot.Int256Slot)
```

Cast an arbitrary slot to a Int256Slot.
### tload

```solidity
function tload(
    TransientSlot.AddressSlot slot
) internal view returns (address value)
```

Load the value held at location `slot` in transient storage.
### tstore

```solidity
function tstore(TransientSlot.AddressSlot slot, address value) internal
```

Store `value` at location `slot` in transient storage.
### tload

```solidity
function tload(
    TransientSlot.BooleanSlot slot
) internal view returns (bool value)
```

Load the value held at location `slot` in transient storage.
### tstore

```solidity
function tstore(TransientSlot.BooleanSlot slot, bool value) internal
```

Store `value` at location `slot` in transient storage.
### tload

```solidity
function tload(
    TransientSlot.Bytes32Slot slot
) internal view returns (bytes32 value)
```

Load the value held at location `slot` in transient storage.
### tstore

```solidity
function tstore(TransientSlot.Bytes32Slot slot, bytes32 value) internal
```

Store `value` at location `slot` in transient storage.
### tload

```solidity
function tload(
    TransientSlot.Uint256Slot slot
) internal view returns (uint256 value)
```

Load the value held at location `slot` in transient storage.
### tstore

```solidity
function tstore(TransientSlot.Uint256Slot slot, uint256 value) internal
```

Store `value` at location `slot` in transient storage.
### tload

```solidity
function tload(
    TransientSlot.Int256Slot slot
) internal view returns (int256 value)
```

Load the value held at location `slot` in transient storage.
### tstore

```solidity
function tstore(TransientSlot.Int256Slot slot, int256 value) internal
```

Store `value` at location `slot` in transient storage.