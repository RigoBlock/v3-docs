# UnlimitedAllowanceToken

## Overview

#### License: Apache 2.0

```solidity
abstract contract UnlimitedAllowanceToken is ERC20
```


## Functions info

### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address from,
    address to,
    uint256 value
) external override returns (bool)
```

ERC20 transferFrom, modified such that an allowance of _MAX_UINT represents an unlimited allowance.


Parameters:

| Name  | Type    | Description                |
| :---- | :------ | :------------------------- |
| from  | address | Address to transfer from.  |
| to    | address | Address to transfer to.    |
| value | uint256 | Amount to transfer.        |


Return values:

| Name | Type | Description          |
| :--- | :--- | :------------------- |
| [0]  | bool | Success of transfer. |
