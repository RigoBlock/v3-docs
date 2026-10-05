# MixinFallback

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinFallback is MixinImmutables, MixinStorage
```


## Errors info

### PoolImplementationDirectCallNotAllowed

```solidity
error PoolImplementationDirectCallNotAllowed()
```


### PoolMethodNotAllowed

```solidity
error PoolMethodNotAllowed()
```


### PoolVersionNotSupported

```solidity
error PoolVersionNotSupported()
```


## Modifiers info

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### fallback

```solidity
fallback() external onlyDelegateCall
```

Delegate calls to pool extension.

Extensions are persistent, while adapters are upgradable by the governance.

uses shouldDelegatecall to flag selectors that should prompt a delegatecall.
Delegatecall restricted to owner, staticcall accessible by everyone.

Restricting delegatecall to owner effectively locks direct calls.
### receive

```solidity
receive() external payable onlyDelegateCall
```

Allows transfers to pool.

Prevents accidental transfer to implementation contract.