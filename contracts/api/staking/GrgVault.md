# GrgVault

## Overview

#### License: Apache 2.0

```solidity
contract GrgVault is Authorizable, IGrgVault
```


## State variables info

### stakingProxy (0x22f80d11)

```solidity
address stakingProxy
```


### isInCatastrophicFailure (0x266df27c)

```solidity
bool isInCatastrophicFailure
```


### grgAssetProxy (0x63e17553)

```solidity
contract IAssetProxy grgAssetProxy
```


## Modifiers info

### onlyStakingProxy

```solidity
modifier onlyStakingProxy()
```

Only stakingProxy can call this function.
### onlyInCatastrophicFailure

```solidity
modifier onlyInCatastrophicFailure()
```

Function can only be called in catastrophic failure mode.
### onlyNotInCatastrophicFailure

```solidity
modifier onlyNotInCatastrophicFailure()
```

Function can only be called not in catastropic failure mode
## Functions info

### constructor

```solidity
constructor(
    address grgProxyAddress,
    address grgTokenAddress,
    address newOwner
) Authorizable(newOwner)
```

Constructor.


Parameters:

| Name            | Type    | Description                          |
| :-------------- | :------ | :----------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy.  |
| grgTokenAddress | address | Address of the Grg Token.            |
| newOwner        | address | Address of the Grg vault owner.      |

### setStakingProxy (0x6bf3f9e5)

```solidity
function setStakingProxy(
    address stakingProxyAddress
) external override onlyAuthorized
```

Sets the address of the StakingProxy contract.
Note that only the contract owner can call this function.


Parameters:

| Name                | Type    | Description                        |
| :------------------ | :------ | :--------------------------------- |
| stakingProxyAddress | address | Address of Staking proxy contract. |

### enterCatastrophicFailure (0xc02e5a7f)

```solidity
function enterCatastrophicFailure()
    external
    override
    onlyAuthorized
    onlyNotInCatastrophicFailure
```

Vault enters into Catastrophic Failure Mode.
*** WARNING - ONCE IN CATOSTROPHIC FAILURE MODE, YOU CAN NEVER GO BACK! ***
Note that only the contract owner can call this function.
### setGrgProxy (0xdb8e54bd)

```solidity
function setGrgProxy(
    address grgProxyAddress
) external override onlyAuthorized onlyNotInCatastrophicFailure
```

Sets the Grg proxy.
Note that only an authorized address can call this function.
Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name            | Type    | Description                         |
| :-------------- | :------ | :---------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy. |

### depositFrom (0x15cc36f2)

```solidity
function depositFrom(
    address staker,
    uint256 amount
) external override onlyStakingProxy onlyNotInCatastrophicFailure
```

Deposit an `amount` of Grg Tokens from `staker` into the vault.
Note that only the Staking contract can call this.
Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description               |
| :----- | :------ | :------------------------ |
| staker | address | of Grg Tokens.            |
| amount | uint256 | of Grg Tokens to deposit. |

### withdrawFrom (0x9470b0bd)

```solidity
function withdrawFrom(
    address staker,
    uint256 amount
) external override onlyStakingProxy onlyNotInCatastrophicFailure
```

Withdraw an `amount` of Grg Tokens to `staker` from the vault.
Note that only the Staking contract can call this.
Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description                |
| :----- | :------ | :------------------------- |
| staker | address | of Grg Tokens.             |
| amount | uint256 | of Grg Tokens to withdraw. |

### withdrawAllFrom (0xf957ddba)

```solidity
function withdrawAllFrom(
    address staker
) external override onlyInCatastrophicFailure returns (uint256)
```

Withdraw ALL Grg Tokens to `staker` from the vault.
Note that this can only be called when *in* Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description    |
| :----- | :------ | :------------- |
| staker | address | of Grg Tokens. |

### balanceOf (0x70a08231)

```solidity
function balanceOf(address staker) external view override returns (uint256)
```

Returns the balance in Grg Tokens of the `staker`


Return values:

| Name | Type    | Description     |
| :--- | :------ | :-------------- |
| [0]  | uint256 | Balance in Grg. |

### balanceOfGrgVault (0x6b6df5aa)

```solidity
function balanceOfGrgVault() external view override returns (uint256)
```

Returns the entire balance of Grg tokens in the vault.