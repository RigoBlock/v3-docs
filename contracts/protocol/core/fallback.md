# fallback

## MixinFallback

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```

### fallback

```solidity
fallback() external payable
```

Delegate calls to pool extension.

_Delegatecall restricted to owner, staticcall accessible by everyone. Restricting delegatecall to owner effectively locks direct calls._

### receive

```solidity
receive() external payable
```

Allows transfers to pool.

_Prevents accidental transfer to implementation contract._

### \_checkDelegateCall

```solidity
function _checkDelegateCall() private view
```

### \_getApplicationAdapter

```solidity
function _getApplicationAdapter(bytes4 selector) private view returns (address)
```

_Returns the address of the application adapter._

#### Parameters

| Name     | Type   | Description                   |
| -------- | ------ | ----------------------------- |
| selector | bytes4 | Hash of the method signature. |

#### Return Values

| Name | Type    | Description                         |
| ---- | ------- | ----------------------------------- |
| \[0] | address | Address of the application adapter. |
