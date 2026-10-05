# RigoblockPoolProxy

## Overview

#### License: Apache-2.0-or-later

```solidity
contract RigoblockPoolProxy is IRigoblockPoolProxy
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Structs info

### ImplementationSlot

```solidity
struct ImplementationSlot {
	address implementation;
}
```


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