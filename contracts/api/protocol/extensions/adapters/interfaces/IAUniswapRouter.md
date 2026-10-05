# IAUniswapRouter

## Overview

#### License: Apache 2.0

```solidity
interface IAUniswapRouter
```


## Events info

### UniV4PositionAdded

```solidity
event UniV4PositionAdded(uint256 indexed tokenId)
```

Emitted when a Uniswap V4 liquidity position token ID is tracked by the pool.


Parameters:

| Name    | Type    | Description                                           |
| :------ | :------ | :---------------------------------------------------- |
| tokenId | uint256 | The ERC-721 token ID of the newly minted V4 position. |

### UniV4PositionRemoved

```solidity
event UniV4PositionRemoved(uint256 indexed tokenId)
```

Emitted when a tracked Uniswap V4 liquidity position token ID is removed.


Parameters:

| Name    | Type    | Description                                     |
| :------ | :------ | :---------------------------------------------- |
| tokenId | uint256 | The ERC-721 token ID of the burned V4 position. |

## Errors info

### RecipientNotSmartPoolOrRouter

```solidity
error RecipientNotSmartPoolOrRouter()
```

Thrown when a command recipient is neither the pool nor the router.
### TransactionDeadlinePassed

```solidity
error TransactionDeadlinePassed()
```

Thrown when executing commands with an expired deadline.
### PositionOwner

```solidity
error PositionOwner()
```

Thrown when the pool is not the position owner.
### UniV4PositionsLimitExceeded

```solidity
error UniV4PositionsLimitExceeded()
```

Thrown when the pool reached maximum number of liquidity positions.
### LiquidityMintHookError

```solidity
error LiquidityMintHookError(address hook)
```

Thrown when a pool hook can access liquidity deltas.
### InsufficientNativeBalance

```solidity
error InsufficientNativeBalance()
```

Thrown when the pool does not hold enough balance.
### PositionDoesNotExist

```solidity
error PositionDoesNotExist()
```

Thrown when the calldata contains both mint and increase for the same tokenId.
### InvalidCommandType

```solidity
error InvalidCommandType(uint256 commandType)
```

Thrown when a universal router command is not supported.


Parameters:

| Name        | Type    | Description                   |
| :---------- | :------ | :---------------------------- |
| commandType | uint256 | The unsupported command byte. |

### UnsupportedAction

```solidity
error UnsupportedAction(uint256 action)
```

Thrown when a v4 swap action inside a V4_SWAP command is not supported.


Parameters:

| Name   | Type    | Description                  |
| :----- | :------ | :--------------------------- |
| action | uint256 | The unsupported action byte. |

## Functions info

### execute (0x3593564c)

```solidity
function execute(
    bytes calldata commands,
    bytes[] calldata inputs,
    uint256 deadline
) external
```

Executes encoded commands along with provided inputs. Reverts if deadline has expired.


Parameters:

| Name     | Type    | Description                                                               |
| :------- | :------ | :------------------------------------------------------------------------ |
| commands | bytes   | A set of concatenated commands, each 1 byte in length.                    |
| inputs   | bytes[] | An array of byte strings containing abi encoded inputs for each command.  |
| deadline | uint256 | The deadline by which the transaction must be executed.                   |

### execute (0x24856bc3)

```solidity
function execute(bytes calldata commands, bytes[] calldata inputs) external
```

Executes encoded commands along with provided inputs.

Only mint call has access to state, will revert with direct calls unless recipient is explicitly set to this.

Parameters:

| Name     | Type    | Description                                                               |
| :------- | :------ | :------------------------------------------------------------------------ |
| commands | bytes   | A set of concatenated commands, each 1 byte in length.                    |
| inputs   | bytes[] | An array of byte strings containing abi encoded inputs for each command.  |

### modifyLiquidities (0xdd46508f)

```solidity
function modifyLiquidities(
    bytes calldata unlockData,
    uint256 deadline
) external
```

Executes a Uniswap V4 Posm liquidity transaction.


Parameters:

| Name       | Type    | Description                                          |
| :--------- | :------ | :--------------------------------------------------- |
| unlockData | bytes   | Encoded calldata containing actions to be executed.  |
| deadline   | uint256 | Deadline of the transaction.                         |
