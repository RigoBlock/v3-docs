# Solidity API

## GrgVault

### stakingProxy

```solidity
address stakingProxy
```

### isInCatastrophicFailure

```solidity
bool isInCatastrophicFailure
```

### \_balances

```solidity
mapping(address => uint256) _balances
```

### grgAssetProxy

```solidity
contract IAssetProxy grgAssetProxy
```

### \_grgToken

```solidity
contract IERC20Token _grgToken
```

### \_grgAssetData

```solidity
bytes _grgAssetData
```

### onlyStakingProxy

```solidity
modifier onlyStakingProxy()
```

_Only stakingProxy can call this function._

### onlyInCatastrophicFailure

```solidity
modifier onlyInCatastrophicFailure()
```

_Function can only be called in catastrophic failure mode._

### onlyNotInCatastrophicFailure

```solidity
modifier onlyNotInCatastrophicFailure()
```

_Function can only be called not in catastropic failure mode_

### constructor

```solidity
constructor(address grgProxyAddress, address grgTokenAddress, address newOwner) public
```

_Constructor._

#### Parameters

| Name            | Type    | Description                         |
| --------------- | ------- | ----------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy. |
| grgTokenAddress | address | Address of the Grg Token.           |
| newOwner        | address | Address of the Grg vault owner.     |

### setStakingProxy

```solidity
function setStakingProxy(address stakingProxyAddress) external
```

_Sets the address of the StakingProxy contract. Note that only the contract owner can call this function._

#### Parameters

| Name                | Type    | Description                        |
| ------------------- | ------- | ---------------------------------- |
| stakingProxyAddress | address | Address of Staking proxy contract. |

### enterCatastrophicFailure

```solidity
function enterCatastrophicFailure() external
```

_Vault enters into Catastrophic Failure Mode. \*\*\* WARNING - ONCE IN CATOSTROPHIC FAILURE MODE, YOU CAN NEVER GO BACK! \*\*\* Note that only the contract owner can call this function._

### setGrgProxy

```solidity
function setGrgProxy(address grgProxyAddress) external
```

_Sets the Grg proxy. Note that only an authorized address can call this function. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name            | Type    | Description                         |
| --------------- | ------- | ----------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy. |

### depositFrom

```solidity
function depositFrom(address staker, uint256 amount) external
```

_Deposit an `amount` of Grg Tokens from `staker` into the vault. Note that only the Staking contract can call this. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description               |
| ------ | ------- | ------------------------- |
| staker | address | of Grg Tokens.            |
| amount | uint256 | of Grg Tokens to deposit. |

### withdrawFrom

```solidity
function withdrawFrom(address staker, uint256 amount) external
```

_Withdraw an `amount` of Grg Tokens to `staker` from the vault. Note that only the Staking contract can call this. Note that this can only be called when not in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | of Grg Tokens.             |
| amount | uint256 | of Grg Tokens to withdraw. |

### withdrawAllFrom

```solidity
function withdrawAllFrom(address staker) external returns (uint256)
```

_Withdraw ALL Grg Tokens to `staker` from the vault. Note that this can only be called when in Catastrophic Failure mode._

#### Parameters

| Name   | Type    | Description    |
| ------ | ------- | -------------- |
| staker | address | of Grg Tokens. |

### balanceOf

```solidity
function balanceOf(address staker) external view returns (uint256)
```

_Returns the balance in Grg Tokens of the `staker`_

#### Return Values

| Name | Type    | Description     |
| ---- | ------- | --------------- |
| \[0] | uint256 | Balance in Grg. |

### balanceOfGrgVault

```solidity
function balanceOfGrgVault() external view returns (uint256)
```

_Returns the entire balance of Grg tokens in the vault._

### \_withdrawFrom

```solidity
function _withdrawFrom(address staker, uint256 amount) internal
```

_Withdraw an `amount` of Grg Tokens to `staker` from the vault._

#### Parameters

| Name   | Type    | Description                |
| ------ | ------- | -------------------------- |
| staker | address | of Grg Tokens.             |
| amount | uint256 | of Grg Tokens to withdraw. |

### \_assertSenderIsStakingProxy

```solidity
function _assertSenderIsStakingProxy() private view
```

_Asserts that sender is stakingProxy contract._

### \_assertInCatastrophicFailure

```solidity
function _assertInCatastrophicFailure() private view
```

_Asserts that vault is in catastrophic failure mode._

### \_assertNotInCatastrophicFailure

```solidity
function _assertNotInCatastrophicFailure() private view
```

_Asserts that vault is not in catastrophic failure mode._
