# EERC20

## Overview

#### License: Apache 2.0

```solidity
contract EERC20 is IEERC20
```

Author: Gabriele Rigo - <gab@rigoblock.com>

Pool tokens are non-transferable: transfer methods revert, allowances are always null.

Called via delegatecall from pool. Kept as an extension to keep the pool implementation

within the contract size limit. Direct calls are harmless: mutating methods revert.
## Errors info

### PoolTokenOperationNotAllowed

```solidity
error PoolTokenOperationNotAllowed()
```


## Functions info

### transfer (0xa9059cbb)

```solidity
function transfer(address, uint256) external override returns (bool)
```

Transfers are not allowed on pool tokens.
### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address,
    address,
    uint256
) external override returns (bool)
```

Transfers are not allowed on pool tokens.
### approve (0x095ea7b3)

```solidity
function approve(address, uint256) external override returns (bool)
```

Approvals are not allowed on pool tokens.
### allowance (0xdd62ed3e)

```solidity
function allowance(address, address) external pure override returns (uint256)
```

Pool tokens do not support allowances.

Always returns 0 by protocol invariant: approve and transferFrom revert, so no

allowance can exist for any (owner, spender) pair. If approvals are ever enabled,

allowance MUST be implemented in the pool implementation — a function implemented

there shadows this routing; leaving it here would silently keep returning 0.