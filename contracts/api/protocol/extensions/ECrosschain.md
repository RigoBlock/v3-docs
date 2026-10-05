# ECrosschain

## Overview

#### License: Apache-2.0-or-later

```solidity
contract ECrosschain is IECrosschain, ReentrancyGuardTransient
```

Author: Gabriele Rigo - <gab@rigoblock.com>
This extension manages NAV integrity when receiving tokens from cross-chain sources.

Called via delegatecall from pool. Can be called by Across messages, Escrow contracts, or anyone with tokens to donate.

Direct calls will fail naturally because the contract does not implement `updateUnitaryValue`.

## Errors info

### CallerTransferAmount

```solidity
error CallerTransferAmount()
```


## Functions info

### donate (0x6da7df96)

```solidity
function donate(
    address token,
    uint256 amount,
    DestinationMessageParams calldata params
) external override nonReentrant
```

Handles receiving tokens from a cross-chain message or an escrow refund.

Called via delegatecall from pool. Callable by anyone.


Parameters:

| Name   | Type                            | Description                                                                    |
| :----- | :------------------------------ | :----------------------------------------------------------------------------- |
| token  | address                         | The token received on this chain.                                              |
| amount | uint256                         | The amount received.                                                           |
| params | struct DestinationMessageParams | The message params from the source calls sent to the across multicall handler. |
