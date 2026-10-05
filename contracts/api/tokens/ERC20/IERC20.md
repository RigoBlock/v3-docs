# IERC20

## Overview

#### License: Apache 2.0

```solidity
interface IERC20
```


## Events info

### Transfer

```solidity
event Transfer(address indexed from, address indexed to, uint256 value)
```

Emitted when a token is transferred.


Parameters:

| Name  | Type    | Description                       |
| :---- | :------ | :-------------------------------- |
| from  | address | Address transferring the tokens.  |
| to    | address | Address receiving the tokens.     |
| value | uint256 | Number of token units.            |

### Approval

```solidity
event Approval(address indexed owner, address indexed spender, uint256 value)
```

Emitted when a token holder sets and approval.


Parameters:

| Name    | Type    | Description                                   |
| :------ | :------ | :-------------------------------------------- |
| owner   | address | Address of the account setting the approval.  |
| spender | address | Address of the allowed account.               |
| value   | uint256 | Number of approved units.                     |

## Functions info

### transfer (0xa9059cbb)

```solidity
function transfer(address to, uint256 value) external returns (bool success)
```

Transfers token from holder to another address.


Parameters:

| Name  | Type    | Description                     |
| :---- | :------ | :------------------------------ |
| to    | address | Address to send tokens to.      |
| value | uint256 | Number of token units to send.  |


Return values:

| Name    | Type | Description                          |
| :------ | :--- | :----------------------------------- |
| success | bool | Bool the transaction was successful. |

### transferFrom (0x23b872dd)

```solidity
function transferFrom(
    address from,
    address to,
    uint256 value
) external returns (bool success)
```

Allows spender to transfer tokens from the holder.


Parameters:

| Name  | Type    | Description                   |
| :---- | :------ | :---------------------------- |
| from  | address | Address of the token holder.  |
| to    | address | Address to send tokens to.    |
| value | uint256 | Number of units to transfer.  |


Return values:

| Name    | Type | Description                          |
| :------ | :--- | :----------------------------------- |
| success | bool | Bool the transaction was successful. |

### approve (0x095ea7b3)

```solidity
function approve(
    address spender,
    uint256 value
) external returns (bool success)
```

Allows a holder to approve a spender.


Parameters:

| Name    | Type    | Description                      |
| :------ | :------ | :------------------------------- |
| spender | address | Address of the token spender.    |
| value   | uint256 | Number of units to be approved.  |


Return values:

| Name    | Type | Description                          |
| :------ | :--- | :----------------------------------- |
| success | bool | Bool the transaction was successful. |

### balanceOf (0x70a08231)

```solidity
function balanceOf(address who) external view returns (uint256)
```

Returns token balance for an address.


Parameters:

| Name | Type    | Description                    |
| :--- | :------ | :----------------------------- |
| who  | address | Address to query balance for.  |


Return values:

| Name | Type    | Description           |
| :--- | :------ | :-------------------- |
| [0]  | uint256 | Number of units held. |

### allowance (0xdd62ed3e)

```solidity
function allowance(
    address owner,
    address spender
) external view returns (uint256)
```

Returns token allowance of an address to another address.


Parameters:

| Name    | Type    | Description                    |
| :------ | :------ | :----------------------------- |
| owner   | address | Address of token hodler.       |
| spender | address | Address of the token spender.  |


Return values:

| Name | Type    | Description              |
| :--- | :------ | :----------------------- |
| [0]  | uint256 | Number of allowed units. |

### totalSupply (0x18160ddd)

```solidity
function totalSupply() external view returns (uint256)
```

Returns the total supply of the token.


Return values:

| Name | Type    | Description             |
| :--- | :------ | :---------------------- |
| [0]  | uint256 | Number of issued units. |
