# IEERC20

## Overview

#### License: Apache 2.0

```solidity
interface IEERC20
```

Author: Gabriele Rigo - <gab@rigoblock.com>

Pool shares are non-transferable: transfer methods always revert and no allowances exist.

balanceOf, decimals, name, symbol and totalSupply are implemented by the pool implementation.
## Functions info

### transfer (0xa9059cbb)

```solidity
function transfer(address to, uint256 value) external returns (bool success)
```

Transfers are not allowed on pool tokens.
### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address from,
    address to,
    uint256 value
) external returns (bool success)
```

Transfers are not allowed on pool tokens.
### approve (0x095ea7b3)

```solidity
function approve(
    address spender,
    uint256 value
) external returns (bool success)
```

Approvals are not allowed on pool tokens.
### allowance (0xdd62ed3e)

```solidity
function allowance(
    address owner,
    address spender
) external view returns (uint256)
```

Pool tokens do not support allowances.

Always returns 0 by protocol invariant: approve and transferFrom revert, so no

allowance can exist for any (owner, spender) pair. If approvals are ever enabled,

allowance MUST be implemented in the pool implementation — a function implemented

there shadows this routing; leaving it here would silently keep returning 0.