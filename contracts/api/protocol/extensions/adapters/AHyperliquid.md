# AHyperliquid

## Overview

#### License: Apache-2.0-or-later

```solidity
contract AHyperliquid is IAHyperliquid, IMinimumVersion, ReentrancyGuardTransient
```

security-contact: security@rigoblock.com
## Modifiers info

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### constructor

```solidity
constructor()
```


### requiredVersion (0x2ea6c3f0)

```solidity
function requiredVersion() external pure override returns (string memory)
```

Returns the minimum implementation version to use an external application.

Adapters must implement it when modifying proxy state or storage.


Return values:

| Name | Type   | Description                              |
| :--- | :----- | :--------------------------------------- |
| [0]  | string | String of the minimum supported version. |

### deposit (0x2b2dfd2c)

```solidity
function deposit(
    uint256 amount,
    uint32 destinationDex
) external override nonReentrant onlyDelegateCall
```


### depositFor (0xc23c545a)

```solidity
function depositFor(
    address recipient,
    uint256 amount,
    uint32 destinationDex
) external override nonReentrant onlyDelegateCall
```


### sendRawAction (0x17938e13)

```solidity
function sendRawAction(
    bytes calldata data
) external override nonReentrant onlyDelegateCall
```

