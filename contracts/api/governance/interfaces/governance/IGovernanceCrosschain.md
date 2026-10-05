# IGovernanceCrosschain

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceCrosschain
```


## Errors info

### GovReceiverInvalidVaa

```solidity
error GovReceiverInvalidVaa(string reason)
```

Thrown when the Wormhole core contract reports an invalid VAA.
### GovReceiverUnknownEmitter

```solidity
error GovReceiverUnknownEmitter()
```

Thrown when the VAA emitter is not the trusted sender-chain governance proxy.
### GovReceiverWrongChain

```solidity
error GovReceiverWrongChain(uint16 targetChainId, uint16 localChainId)
```

Thrown when the VAA is intended for a different target chain.
### GovReceiverLocalEmitter

```solidity
error GovReceiverLocalEmitter(uint16 chainId)
```

Thrown when the receiver would accept messages from its own chain.
### GovReceiverInvalidSequence

```solidity
error GovReceiverInvalidSequence(uint64 sequence, uint64 nextMinimumSequence)
```

Thrown when the VAA sequence is lower than the next minimum sequence.
### GovReceiverMessageExpired

```solidity
error GovReceiverMessageExpired(uint64 sequence)
```

Thrown when the VAA is older than the execution window.
### GovReceiverNotConfigured

```solidity
error GovReceiverNotConfigured()
```

Thrown when the governance strategy has no Wormhole address configured.
## Functions info

### receiveMessage (0xf953cec7)

```solidity
function receiveMessage(bytes memory encodedMessage) external
```

Consumes a Wormhole VAA and executes the governance actions it contains.

Sequences must be strictly monotonically increasing but need not be consecutive:
a message that reverts is never consumed and can be skipped by delivering any
later message. A failing action reverts the whole message with the target's
return data.


Parameters:

| Name           | Type  | Description                 |
| :------------- | :---- | :-------------------------- |
| encodedMessage | bytes | The raw verified VAA bytes. |

### nextMinimumSequence (0x7b305b32)

```solidity
function nextMinimumSequence() external view returns (uint64)
```

Minimum Wormhole sequence accepted by the next `receiveMessage` call.