# Solidity API

## RigoblockPoolProxy

### \_IMPLEMENTATION\_SLOT

```solidity
bytes32 _IMPLEMENTATION_SLOT
```

### constructor

```solidity
constructor() public payable
```

Sets address of implementation contract.

### fallback

```solidity
fallback() external payable
```

Fallback function forwards all transactions and returns all received return data.

### ImplementationSlot

```solidity
struct ImplementationSlot {
  address implementation;
}
```

### getImplementation

```solidity
function getImplementation() private pure returns (struct RigoblockPoolProxy.ImplementationSlot s)
```

Method to read/write from/to implementation slot.

#### Return Values

| Name | Type                                         | Description                              |
| ---- | -------------------------------------------- | ---------------------------------------- |
| s    | struct RigoblockPoolProxy.ImplementationSlot | Storage slot of the pool implementation. |
