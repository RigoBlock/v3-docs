# IAIntents

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IAIntents
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Structs info

### AcrossParams

```solidity
struct AcrossParams {
	address depositor;
	address recipient;
	address inputToken;
	address outputToken;
	uint256 inputAmount;
	uint256 outputAmount;
	uint256 destinationChainId;
	address exclusiveRelayer;
	uint32 quoteTimestamp;
	uint32 fillDeadline;
	uint32 exclusivityDeadline;
	bytes message;
}
```


## Events info

### CrossChainTransferInitiated

```solidity
event CrossChainTransferInitiated(address indexed from, uint256 indexed destinationChainId, address indexed inputToken, uint256 inputAmount, uint8 opType, address escrow)
```

Emitted when tokens are deposited for cross-chain transfer


Parameters:

| Name               | Type    | Description                          |
| :----------------- | :------ | :----------------------------------- |
| from               | address | Address that initiated the transfer  |
| destinationChainId | uint256 | Destination chain ID                 |
| inputToken         | address | Token being sent                     |
| inputAmount        | uint256 | Amount sent                          |
| opType             | uint8   | Operation type (0=Transfer, 1=Sync)  |
| escrow             | address | Escrow address receiving refunds     |

## Errors info

### DirectCallNotAllowed

```solidity
error DirectCallNotAllowed()
```


### NullAddress

```solidity
error NullAddress()
```


### ZeroConvertedValue

```solidity
error ZeroConvertedValue()
```


### OutputAmountTooHigh

```solidity
error OutputAmountTooHigh()
```


### OutputAmountTooLow

```solidity
error OutputAmountTooLow()
```


### TokenNotActive

```solidity
error TokenNotActive()
```


### SameChainTransfer

```solidity
error SameChainTransfer()
```


### InvalidInputToken

```solidity
error InvalidInputToken()
```


## Functions info

### depositV3 (0x770d096f)

```solidity
function depositV3(IAIntents.AcrossParams memory params) external
```

Executes a crosschain token transfer to across and updated virtual storage.

Has different method selector than across depositV3 to avoid viaIr compilation.


Parameters:

| Name   | Type                          | Description                     |
| :----- | :---------------------------- | :------------------------------ |
| params | struct IAIntents.AcrossParams | Across params encoded as tuple. |
