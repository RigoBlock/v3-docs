# IA0xRouter

## Overview

#### License: Apache 2.0

```solidity
interface IA0xRouter
```

Author: Gabriele Rigo - <gab@rigoblock.com>
Allows Rigoblock smart pools to execute swaps via the 0x AllowanceHolder and Settler contracts.

## Errors info

### DirectCallNotAllowed

```solidity
error DirectCallNotAllowed()
```

Thrown when a call is made directly to the adapter instead of via delegatecall.
### RecipientNotSmartPool

```solidity
error RecipientNotSmartPool()
```

Thrown when the swap recipient is not the smart pool.
### CounterfeitSettler

```solidity
error CounterfeitSettler(address target)
```

Thrown when the target is not a genuine 0x Settler instance.
### UnsupportedSettlerFunction

```solidity
error UnsupportedSettlerFunction()
```

Thrown when the Settler calldata has an unsupported function selector.
### InvalidSettlerCalldata

```solidity
error InvalidSettlerCalldata()
```

Thrown when the Settler calldata is too short to decode.
### InsufficientNativeBalance

```solidity
error InsufficientNativeBalance()
```

Thrown when the pool does not hold enough native balance.
### OperatorMustEqualTarget

```solidity
error OperatorMustEqualTarget()
```

Thrown when operator is not the same address as target.

AllowanceHolder stores the ephemeral allowance under `operator`. If operator differs
from the genuine Settler (target), a malicious operator contract could consume the
ephemeral allowance and drain pool tokens to an arbitrary address.
### TransferFromRecipientNotSettler

```solidity
error TransferFromRecipientNotSettler(address recipient)
```

Thrown when a TRANSFER_FROM action's recipient is not the Settler itself.

Allowing an arbitrary recipient would let the pool owner drain funds.


Parameters:

| Name      | Type    | Description                                          |
| :-------- | :------ | :--------------------------------------------------- |
| recipient | address | The decoded recipient address that failed the check. |

## Functions info

### exec (0x2213bc0b)

```solidity
function exec(
    address operator,
    address token,
    uint256 amount,
    address payable target,
    bytes calldata data
) external payable returns (bytes memory result)
```

Execute a swap via the 0x AllowanceHolder contract.

The calldata is forwarded unmodified to AllowanceHolder after validation.


Parameters:

| Name     | Type            | Description                                                                      |
| :------- | :-------------- | :------------------------------------------------------------------------------- |
| operator | address         | The address authorized to consume the ephemeral allowance. Must equal `target`.  |
| token    | address         | The sell token address.                                                          |
| amount   | uint256         | The sell token amount.                                                           |
| target   | address payable | The 0x Settler contract address that will execute the swap.                      |
| data     | bytes           | The Settler.execute() calldata containing swap instructions.                     |


Return values:

| Name   | Type  | Description                                |
| :----- | :---- | :----------------------------------------- |
| result | bytes | The return data from AllowanceHolder.exec. |
