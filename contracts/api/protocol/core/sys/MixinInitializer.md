# MixinInitializer

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinInitializer is MixinImmutables, MixinStorage
```


## Errors info

### BaseTokenDecimals

```solidity
error BaseTokenDecimals()
```


### PoolAlreadyInitialized

```solidity
error PoolAlreadyInitialized()
```


## Modifiers info

### onlyUninitialized

```solidity
modifier onlyUninitialized()
```


## Functions info

### initializePool (0x250e6de0)

```solidity
function initializePool() external override onlyUninitialized
```

Initializes to pool storage.

Cannot be reentered as no non-view call is performed to external contracts. Unlocked is kept for backwards compatibility.
Pool can only be initialized at creation, meaning this method cannot be called directly to implementation.