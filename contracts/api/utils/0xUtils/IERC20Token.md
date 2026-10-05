# IERC20Token

## Overview

#### License: Apache 2.0

```solidity
abstract contract IERC20Token
```


## Events info

### Transfer

```solidity
event Transfer(address indexed _from, address indexed _to, uint256 _value)
```


### Approval

```solidity
event Approval(address indexed _owner, address indexed _spender, uint256 _value)
```


## Functions info

### transfer (0xa9059cbb)

```solidity
function transfer(address _to, uint256 _value) external virtual returns (bool)
```

send `value` token to `to` from `msg.sender`


Parameters:

| Name   | Type    | Description                            |
| :----- | :------ | :------------------------------------- |
| _to    | address | The address of the recipient           |
| _value | uint256 | The amount of token to be transferred  |


Return values:

| Name | Type | Description                     |
| :--- | :--- | :------------------------------ |
| [0]  | bool | True if transfer was successful |

### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address _from,
    address _to,
    uint256 _value
) external virtual returns (bool)
```

send `value` token to `to` from `from` on the condition it is approved by `from`


Parameters:

| Name   | Type    | Description                            |
| :----- | :------ | :------------------------------------- |
| _from  | address | The address of the sender              |
| _to    | address | The address of the recipient           |
| _value | uint256 | The amount of token to be transferred  |


Return values:

| Name | Type | Description                     |
| :--- | :--- | :------------------------------ |
| [0]  | bool | True if transfer was successful |

### approve (0x095ea7b3)

```solidity
function approve(
    address _spender,
    uint256 _value
) external virtual returns (bool)
```

`msg.sender` approves `_spender` to spend `_value` tokens


Parameters:

| Name     | Type    | Description                                             |
| :------- | :------ | :------------------------------------------------------ |
| _spender | address | The address of the account able to transfer the tokens  |
| _value   | uint256 | The amount of wei to be approved for transfer           |


Return values:

| Name | Type | Description                                                  |
| :--- | :--- | :----------------------------------------------------------- |
| [0]  | bool | Always true if the call has enough gas to complete execution |

### totalSupply (0x18160ddd)

```solidity
function totalSupply() external view virtual returns (uint256)
```

Query total supply of token


Return values:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| [0]  | uint256 | Total supply of token |

### balanceOf (0x70a08231)

```solidity
function balanceOf(address _owner) external view virtual returns (uint256)
```



Parameters:

| Name   | Type    | Description                                           |
| :----- | :------ | :---------------------------------------------------- |
| _owner | address | The address from which the balance will be retrieved  |


Return values:

| Name | Type    | Description      |
| :--- | :------ | :--------------- |
| [0]  | uint256 | Balance of owner |

### allowance (0xdd62ed3e)

```solidity
function allowance(
    address _owner,
    address _spender
) external view virtual returns (uint256)
```



Parameters:

| Name     | Type    | Description                                             |
| :------- | :------ | :------------------------------------------------------ |
| _owner   | address | The address of the account owning tokens                |
| _spender | address | The address of the account able to transfer the tokens  |


Return values:

| Name | Type    | Description                                 |
| :--- | :------ | :------------------------------------------ |
| [0]  | uint256 | Amount of remaining tokens allowed to spent |
