# EscrowFactory

## Overview

#### License: Apache-2.0-or-later

```solidity
library EscrowFactory
```

Creates escrow contracts using CREATE2 for deterministic addresses

Escrow contracts are deployed per pool and operation type
## Events info

### EscrowDeployed

```solidity
event EscrowDeployed(address indexed pool, OpType indexed opType, address escrowContract)
```

Emitted when a new escrow contract is deployed
## Errors info

### DeploymentFailed

```solidity
error DeploymentFailed()
```


## Functions info

### getEscrowAddress

```solidity
function getEscrowAddress(
    address pool,
    OpType opType
) internal pure returns (address escrowAddress)
```

Gets the deterministic address for an escrow contract


Parameters:

| Name   | Type        | Description         |
| :----- | :---------- | :------------------ |
| pool   | address     | The pool address    |
| opType | enum OpType | The operation type  |


Return values:

| Name          | Type    | Description               |
| :------------ | :------ | :------------------------ |
| escrowAddress | address | The deterministic address |

### deployEscrow

```solidity
function deployEscrow(
    address pool,
    OpType opType
) internal returns (address escrowContract)
```

Deploys an escrow contract using CREATE2 (idempotent)

MUST be called via delegatecall from pool context (address(this) == pool)

Parameters:

| Name   | Type        | Description         |
| :----- | :---------- | :------------------ |
| pool   | address     | The pool address    |
| opType | enum OpType | The operation type  |


Return values:

| Name           | Type    | Description                           |
| :------------- | :------ | :------------------------------------ |
| escrowContract | address | The deployed escrow contract address  |
