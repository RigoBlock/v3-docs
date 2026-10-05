# RigoblockGovernanceProxy

## Overview

#### License: Apache-2.0

```solidity
contract RigoblockGovernanceProxy
```


## Structs info

### ImplementationSlot

```solidity
struct ImplementationSlot {
	address implementation;
}
```


## Events info

### Upgraded

```solidity
event Upgraded(address indexed newImplementation)
```

Emitted when implementation written to proxy storage.

Emitted also at first variable initialization.


Parameters:

| Name              | Type    | Description                        |
| :---------------- | :------ | :--------------------------------- |
| newImplementation | address | Address of the new implementation. |

## Functions info

### constructor

```solidity
constructor() payable
```

Sets address of implementation contract.
### fallback

```solidity
fallback() external payable
```

Fallback function forwards all transactions and returns all received return data.
### receive

```solidity
receive() external payable
```

Allows this contract to receive ether.