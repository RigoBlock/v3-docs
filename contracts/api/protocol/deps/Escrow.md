# Escrow

## Overview

#### License: Apache-2.0-or-later

```solidity
contract Escrow is ReentrancyGuardTransient
```

Manages refunds to pool via escrow, like across expired deposits.

Deployed per pool per OpType via CREATE2 for deterministic addressing
## Events info

### TokensDonated

```solidity
event TokensDonated(address indexed token, uint256 amount)
```

Emitted when tokens are donated back to the pool
## Errors info

### InvalidAmount

```solidity
error InvalidAmount()
```


### InvalidPool

```solidity
error InvalidPool()
```


### UnsupportedToken

```solidity
error UnsupportedToken()
```


## State variables info

### pool (0x16f0115b)

```solidity
address immutable pool
```

The pool this escrow is associated with
### opType (0x95dea912)

```solidity
enum OpType immutable opType
```

The operation type this escrow handles (Transfer or Sync)
## Functions info

### constructor

```solidity
constructor(address _pool, OpType _opType)
```

The passed pool must be a Rigoblock pool, i.e. implement `donate` with unlock.
### refundVault (0x5a53eecd)

```solidity
function refundVault(address token) external nonReentrant
```

Allows anyone to send owned to the target Rigoblock pool.


Parameters:

| Name  | Type    | Description                 |
| :---- | :------ | :-------------------------- |
| token | address | The token address to claim. |
