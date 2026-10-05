# LibSafeDowncast

## Overview

#### License: Apache 2.0

```solidity
library LibSafeDowncast
```


## Functions info

### downcastToUint96

```solidity
function downcastToUint96(uint256 a) internal pure returns (uint96 b)
```

Safely downcasts to a uint96
Note that this reverts if the input value is too large.
### downcastToUint64

```solidity
function downcastToUint64(uint256 a) internal pure returns (uint64 b)
```

Safely downcasts to a uint64
Note that this reverts if the input value is too large.