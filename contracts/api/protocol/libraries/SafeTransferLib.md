# SafeTransferLib

## Overview

#### License: Apache3.0-or-later

```solidity
library SafeTransferLib
```

This library allows for safe transfer of tokens without using assembly
## Errors info

### ApprovalFailed

```solidity
error ApprovalFailed(address token)
```


### NativeTransferFailed

```solidity
error NativeTransferFailed()
```


### TokenTransferFailed

```solidity
error TokenTransferFailed()
```


### TokenTransferFromFailed

```solidity
error TokenTransferFromFailed()
```


### ApprovalTargetIsNotContract

```solidity
error ApprovalTargetIsNotContract(address token)
```


## Functions info

### safeTransferNative

```solidity
function safeTransferNative(address to, uint256 amount) internal
```


### safeTransfer

```solidity
function safeTransfer(address token, address to, uint256 amount) internal
```


### safeTransferFrom

```solidity
function safeTransferFrom(
    address token,
    address from,
    address to,
    uint256 amount
) internal
```


### safeApprove

```solidity
function safeApprove(address token, address spender, uint256 amount) internal
```

Allows approving all ERC20 tokens, forcing approvals when needed.
### isAddressZero

```solidity
function isAddressZero(address target) internal pure returns (bool)
```

