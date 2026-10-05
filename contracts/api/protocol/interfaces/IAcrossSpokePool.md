# IAcrossSpokePool

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IAcrossSpokePool
```

Interface for Across Protocol V3 SpokePool contract

Used for cross-chain token transfers via Across Protocol
## Functions info

### fillDeadlineBuffer (0x079bd2c7)

```solidity
function fillDeadlineBuffer() external view returns (uint32)
```


### depositV3 (0x7b939232)

```solidity
function depositV3(
    address depositor,
    address recipient,
    address inputToken,
    address outputToken,
    uint256 inputAmount,
    uint256 outputAmount,
    uint256 destinationChainId,
    address exclusiveRelayer,
    uint32 quoteTimestamp,
    uint32 fillDeadline,
    uint32 exclusivityDeadline,
    bytes calldata message
) external payable
```

