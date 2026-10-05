# MixinInitializer

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinInitializer is MixinStorage
```


## Errors info

### GovAlreadyInitialized

```solidity
error GovAlreadyInitialized()
```


### InitParamsVerification

```solidity
error InitParamsVerification()
```


## Modifiers info

### onlyUninitialized

```solidity
modifier onlyUninitialized()
```


## Functions info

### initializeGovernance (0xe9134903)

```solidity
function initializeGovernance() external override onlyUninitialized
```

Initializes the Rigoblock Governance.

Params are stored in factory and read from there.