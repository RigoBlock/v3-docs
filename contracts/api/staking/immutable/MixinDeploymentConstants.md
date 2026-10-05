# MixinDeploymentConstants

## Overview

#### License: Apache 2.0

```solidity
abstract contract MixinDeploymentConstants is IStaking
```


## Functions info

### getGrgContract (0xef4ba680)

```solidity
function getGrgContract() public view virtual override returns (IRigoToken)
```

An overridable way to access the deployed GRG contract.

Must be view to allow overrides to access state.


Return values:

| Name | Type                | Description                |
| :--- | :------------------ | :------------------------- |
| [0]  | contract IRigoToken | The GRG contract instance. |

### getGrgVault (0xe0822db7)

```solidity
function getGrgVault() public view virtual override returns (IGrgVault)
```

An overridable way to access the deployed grgVault.

Must be view to allow overrides to access state.


Return values:

| Name | Type               | Description             |
| :--- | :----------------- | :---------------------- |
| [0]  | contract IGrgVault | The GRG vault contract. |

### getPoolRegistry (0x7a9bd5e4)

```solidity
function getPoolRegistry() public view virtual override returns (IPoolRegistry)
```

An overridable way to access the deployed rigoblock pool registry.

Must be view to allow overrides to access state.


Return values:

| Name | Type                   | Description                 |
| :--- | :--------------------- | :-------------------------- |
| [0]  | contract IPoolRegistry | The pool registry contract. |
