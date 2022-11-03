# Solidity API

## ASelfCustody

### grgVault

```solidity
address grgVault
```

Returns the address of the GRG vault contract.

#### Return Values

### \_MINIMUM\_GRG\_STAKE

```solidity
uint128 _MINIMUM_GRG_STAKE
```

### \_TRANSFER\_SELECTOR

```solidity
bytes4 _TRANSFER_SELECTOR
```

### \_stakingProxy

```solidity
address _stakingProxy
```

### \_aSelfCustody

```solidity
address _aSelfCustody
```

### constructor

```solidity
constructor(address newGrgVault, address newStakingProxy) public
```

### transferToSelfCustody

```solidity
function transferToSelfCustody(address payable selfCustodyAccount, address token, uint256 amount) external returns (uint256 shortfall)
```

transfers ETH or tokens to self custody.

#### Parameters

| Name               | Type            | Description                    |
| ------------------ | --------------- | ------------------------------ |
| selfCustodyAccount | address payable | Address of the target account. |
| token              | address         | Address of the target token.   |
| amount             | uint256         | Number of tokens.              |

#### Return Values

| Name      | Type    | Description                            |
| --------- | ------- | -------------------------------------- |
| shortfall | uint256 | Number of GRG pool operator shortfall. |

### poolGrgShortfall

```solidity
function poolGrgShortfall(address targetPool) public view returns (uint256)
```

external check if minimum pool GRG amount requirement satisfied.

#### Parameters

| Name       | Type    | Description |
| ---------- | ------- | ----------- |
| targetPool | address |             |

#### Return Values

| Name | Type    | Description                            |
| ---- | ------- | -------------------------------------- |
| \[0] | uint256 | Number of GRG pool operator shortfall. |

### \_safeTransfer

```solidity
function _safeTransfer(address token, address to, uint256 value) private
```

_executes a safe transfer to any ERC20 token_

#### Parameters

| Name  | Type    | Description           |
| ----- | ------- | --------------------- |
| token | address | Address of the origin |
| to    | address | Address of the target |
| value | uint256 | Amount to transfer    |

### \_getGrgStakingProxy

```solidity
function _getGrgStakingProxy() private view returns (address)
```

### \_getMinimumGrgStake

```solidity
function _getMinimumGrgStake() private pure returns (uint256)
```
