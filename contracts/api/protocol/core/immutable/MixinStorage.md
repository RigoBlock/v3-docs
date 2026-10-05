# MixinStorage

## Overview

#### License: Apache 2.0-or-later

```solidity
abstract contract MixinStorage is MixinImmutables
```

Storage slots must be preserved to prevent storage clashing.

Pool storage is not sequential: each variable is wrapped into a struct which is assigned a storage slot.
## Structs info

### Accounts

```solidity
struct Accounts {
	mapping(address => ISmartPoolState.UserAccount) userAccounts;
}
```


### PoolWrapper

```solidity
struct PoolWrapper {
	Pool pool;
}
```

Pool initialization struct wrapper.

Allows initializing pool as struct for better readability.


Parameters:

| Name | Type        | Description      |
| :--- | :---------- | :--------------- |
| pool | struct Pool | The pool struct. |

### Operator

```solidity
struct Operator {
	mapping(address => mapping(address => bool)) isApproved;
}
```

