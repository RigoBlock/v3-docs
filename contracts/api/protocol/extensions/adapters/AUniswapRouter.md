# AUniswapRouter

## Overview

#### License: Apache-2.0-or-later

```solidity
contract AUniswapRouter is IAUniswapRouter, IMinimumVersion, AUniswapDecoder, ReentrancyGuardTransient
```

Author: Gabriele Rigo - <gab@rigoblock.com>
This contract is used as a bridge between a Rigoblock smart pool contract and the Uniswap universal router.

This contract ensures that tokens approvals are set and removed correctly, and that recipient and tokens are validated.

## Errors info

### DirectCallNotAllowed

```solidity
error DirectCallNotAllowed()
```

Thrown when a call is made to the adapter directly.
## Modifiers info

### checkDeadline

```solidity
modifier checkDeadline(uint256 deadline)
```


### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### constructor

```solidity
constructor(
    address universalRouter,
    address v4Posm,
    address weth
) AUniswapDecoder(weth, v4Posm)
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

### execute (0x3593564c)

```solidity
function execute(
    bytes calldata commands,
    bytes[] calldata inputs,
    uint256 deadline
) external override checkDeadline(deadline)
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
function execute(
    bytes calldata commands,
    bytes[] calldata inputs
) public override nonReentrant onlyDelegateCall
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
) external override onlyDelegateCall
```

Is not reentrancy-protected, as will revert in PositionManager.

Delegatecall-only for extra safety, to pervent accidental user liquidity locking.

Parameters:

| Name       | Type    | Description                                          |
| :--------- | :------ | :--------------------------------------------------- |
| unlockData | bytes   | Encoded calldata containing actions to be executed.  |
| deadline   | uint256 | Deadline of the transaction.                         |
