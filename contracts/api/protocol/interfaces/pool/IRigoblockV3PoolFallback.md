# IRigoblockV3PoolFallback

## Overview

#### License: Apache 2.0

```solidity
interface IRigoblockV3PoolFallback
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### fallback

```solidity
fallback() external payable
```

Delegate calls to pool extension.

Delegatecall restricted to owner, staticcall accessible by everyone.

Restricting delegatecall to owner effectively locks direct calls.
### receive

```solidity
receive() external payable
```

Allows transfers to pool.

Prevents accidental transfer to implementation contract.