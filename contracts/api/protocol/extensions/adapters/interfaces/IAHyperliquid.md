# IAHyperliquid

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IAHyperliquid is ICoreWriter, ICoreDepositWallet
```


## Events info

### ActionSent

```solidity
event ActionSent(uint24 indexed actionId)
```


### Deposited

```solidity
event Deposited(uint256 amount, uint32 destinationDex)
```


## Errors info

### DirectCallNotAllowed

```solidity
error DirectCallNotAllowed()
```


### NotHyperEVM

```solidity
error NotHyperEVM()
```


### InvalidAmount

```solidity
error InvalidAmount()
```


### InvalidDex

```solidity
error InvalidDex()
```


### InvalidActionData

```solidity
error InvalidActionData()
```


### UnsupportedAction

```solidity
error UnsupportedAction(uint24 actionId)
```


### AccountNotActivated

```solidity
error AccountNotActivated()
```


### InsufficientBridgeReserve

```solidity
error InsufficientBridgeReserve()
```

