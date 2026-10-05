# MixinCrosschain

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinCrosschain is MixinStorage
```

Executes actions decided by the sender-chain governance and delivered through Wormhole.
## Functions info

### receiveMessage (0xf953cec7)

```solidity
function receiveMessage(bytes memory encodedMessage) external override
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
function nextMinimumSequence() external view override returns (uint64)
```

Minimum Wormhole sequence accepted by the next `receiveMessage` call.