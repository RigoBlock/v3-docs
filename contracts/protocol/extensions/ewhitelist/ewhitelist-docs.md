# Solidity API

## EWhitelist

This contract has its own storage, which could potentially clash with pool storage if the allocated slot were already used by the implementation. Warning: careful with upgrades as pool only accesses isWhitelistedToken view method. Other methods are locked and should never be approved by governance.

### \_EWHITELIST\_TOKEN\_WHITELIST\_SLOT

```solidity
bytes32 _EWHITELIST_TOKEN_WHITELIST_SLOT
```

### authority

```solidity
address authority
```

### WhitelistSlot

```solidity
struct WhitelistSlot {
  mapping(address => bool) isWhitelisted;
}
```

### onlyAuthorized

```solidity
modifier onlyAuthorized()
```

### constructor

```solidity
constructor(address newAuthority) public
```

### whitelistToken

```solidity
function whitelistToken(address token) public
```

Allows a whitelister to whitelist a token.

#### Parameters

| Name  | Type    | Description                  |
| ----- | ------- | ---------------------------- |
| token | address | Address of the target token. |

### removeToken

```solidity
function removeToken(address token) public
```

Allows a whitelister to remove a token.

#### Parameters

| Name  | Type    | Description                  |
| ----- | ------- | ---------------------------- |
| token | address | Address of the target token. |

### batchUpdateTokens

```solidity
function batchUpdateTokens(address[] tokens, bool[] whitelisted) external
```

Allows a whitelister to whitelist/remove a list of tokens.

#### Parameters

| Name        | Type       | Description                                              |
| ----------- | ---------- | -------------------------------------------------------- |
| tokens      | address\[] | Address array to tokens.                                 |
| whitelisted | bool\[]    | Bollean array the token is to be whitelisted or removed. |

### isWhitelistedToken

```solidity
function isWhitelistedToken(address token) external view returns (bool)
```

Returns whether a token has been whitelisted.

#### Parameters

| Name  | Type    | Description                  |
| ----- | ------- | ---------------------------- |
| token | address | Address of the target token. |

#### Return Values

| Name | Type | Description                       |
| ---- | ---- | --------------------------------- |
| \[0] | bool | Boolean the token is whitelisted. |

### getAuthority

```solidity
function getAuthority() public view returns (address)
```

Returns the address of the authority contract.

#### Return Values

| Name | Type    | Description                        |
| ---- | ------- | ---------------------------------- |
| \[0] | address | Address of the authority contract. |

### \_getWhitelistSlot

```solidity
function _getWhitelistSlot() internal pure returns (struct EWhitelist.WhitelistSlot s)
```

### \_assertCallerIsAuthorized

```solidity
function _assertCallerIsAuthorized() private view
```

### \_isContract

```solidity
function _isContract(address target) private view returns (bool)
```
