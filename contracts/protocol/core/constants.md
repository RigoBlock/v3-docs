# constants

## MixinConstants

Constants are copied in the bytecode and not assigned a storage slot, can safely be added to this contract.

_Inheriting from interface is required as we override public variables._

### VERSION

```solidity
string VERSION
```

Returns a string of the pool version.

#### Return Values

### \_POOL\_INIT\_SLOT

```solidity
bytes32 _POOL_INIT_SLOT
```

### \_POOL\_VARIABLES\_SLOT

```solidity
bytes32 _POOL_VARIABLES_SLOT
```

### \_POOL\_TOKENS\_SLOT

```solidity
bytes32 _POOL_TOKENS_SLOT
```

### \_POOL\_ACCOUNTS\_SLOT

```solidity
bytes32 _POOL_ACCOUNTS_SLOT
```

### \_FEE\_BASE

```solidity
uint16 _FEE_BASE
```

### \_INITIAL\_SPREAD

```solidity
uint16 _INITIAL_SPREAD
```

### \_MAX\_SPREAD

```solidity
uint16 _MAX_SPREAD
```

### \_MAX\_TRANSACTION\_FEE

```solidity
uint16 _MAX_TRANSACTION_FEE
```

### \_MINIMUM\_ORDER\_DIVISOR

```solidity
uint16 _MINIMUM_ORDER_DIVISOR
```

### \_SPREAD\_BASE

```solidity
uint16 _SPREAD_BASE
```

### \_MAX\_LOCKUP

```solidity
uint48 _MAX_LOCKUP
```

### \_MIN\_LOCKUP

```solidity
uint48 _MIN_LOCKUP
```

### \_TRANSFER\_FROM\_SELECTOR

```solidity
bytes4 _TRANSFER_FROM_SELECTOR
```

### \_TRANSFER\_SELECTOR

```solidity
bytes4 _TRANSFER_SELECTOR
```
