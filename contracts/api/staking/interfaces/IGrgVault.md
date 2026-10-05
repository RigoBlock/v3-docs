# IGrgVault

## Overview

#### License: Apache 2.0

```solidity
interface IGrgVault
```


## Events info

### StakingProxySet

```solidity
event StakingProxySet(address stakingProxyAddress)
```

Emmitted whenever a StakingProxy is set in a vault.


Parameters:

| Name                | Type    | Description                            |
| :------------------ | :------ | :------------------------------------- |
| stakingProxyAddress | address | Address of the staking proxy contract. |

### InCatastrophicFailureMode

```solidity
event InCatastrophicFailureMode(address sender)
```

Emitted when the Staking contract is put into Catastrophic Failure Mode


Parameters:

| Name   | Type    | Description                      |
| :----- | :------ | :------------------------------- |
| sender | address | Address of sender (`msg.sender`) |

### Deposit

```solidity
event Deposit(address indexed staker, uint256 amount)
```

Emitted when Grg Tokens are deposited into the vault.


Parameters:

| Name   | Type    | Description                 |
| :----- | :------ | :-------------------------- |
| staker | address | Address of the Grg staker.  |
| amount | uint256 | of Grg Tokens deposited.    |

### Withdraw

```solidity
event Withdraw(address indexed staker, uint256 amount)
```

Emitted when Grg Tokens are withdrawn from the vault.


Parameters:

| Name   | Type    | Description                 |
| :----- | :------ | :-------------------------- |
| staker | address | Address of the Grg staker.  |
| amount | uint256 | of Grg Tokens withdrawn.    |

### GrgProxySet

```solidity
event GrgProxySet(address grgProxyAddress)
```

Emitted whenever the Grg AssetProxy is set.


Parameters:

| Name            | Type    | Description                        |
| :-------------- | :------ | :--------------------------------- |
| grgProxyAddress | address | Address of the Grg transfer proxy. |

## Functions info

### setStakingProxy (0x6bf3f9e5)

```solidity
function setStakingProxy(address stakingProxyAddress) external
```

Sets the address of the StakingProxy contract.

Note that only the contract staker can call this function.


Parameters:

| Name                | Type    | Description                        |
| :------------------ | :------ | :--------------------------------- |
| stakingProxyAddress | address | Address of Staking proxy contract. |

### enterCatastrophicFailure (0xc02e5a7f)

```solidity
function enterCatastrophicFailure() external
```

Vault enters into Catastrophic Failure Mode.

*** WARNING - ONCE IN CATOSTROPHIC FAILURE MODE, YOU CAN NEVER GO BACK! ***

Note that only the contract staker can call this function.
### setGrgProxy (0xdb8e54bd)

```solidity
function setGrgProxy(address grgProxyAddress) external
```

Sets the Grg proxy.

Note that only the contract staker can call this.

Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name            | Type    | Description                         |
| :-------------- | :------ | :---------------------------------- |
| grgProxyAddress | address | Address of the RigoBlock Grg Proxy. |

### depositFrom (0x15cc36f2)

```solidity
function depositFrom(address staker, uint256 amount) external
```

Deposit an `amount` of Grg Tokens from `staker` into the vault.

Note that only the Staking contract can call this.

Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description                 |
| :----- | :------ | :-------------------------- |
| staker | address | Address of the Grg staker.  |
| amount | uint256 | of Grg Tokens to deposit.   |

### withdrawFrom (0x9470b0bd)

```solidity
function withdrawFrom(address staker, uint256 amount) external
```

Withdraw an `amount` of Grg Tokens to `staker` from the vault.

Note that only the Staking contract can call this.

Note that this can only be called when *not* in Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description                 |
| :----- | :------ | :-------------------------- |
| staker | address | Address of the Grg staker.  |
| amount | uint256 | of Grg Tokens to withdraw.  |

### withdrawAllFrom (0xf957ddba)

```solidity
function withdrawAllFrom(address staker) external returns (uint256)
```

Withdraw ALL Grg Tokens to `staker` from the vault.

Note that this can only be called when *in* Catastrophic Failure mode.


Parameters:

| Name   | Type    | Description                |
| :----- | :------ | :------------------------- |
| staker | address | Address of the Grg staker. |

### balanceOf (0x70a08231)

```solidity
function balanceOf(address staker) external view returns (uint256)
```

Returns the balance in Grg Tokens of the `staker`


Parameters:

| Name   | Type    | Description                 |
| :----- | :------ | :-------------------------- |
| staker | address | Address of the Grg staker.  |


Return values:

| Name | Type    | Description     |
| :--- | :------ | :-------------- |
| [0]  | uint256 | Balance in Grg. |

### balanceOfGrgVault (0x6b6df5aa)

```solidity
function balanceOfGrgVault() external view returns (uint256)
```

Returns the entire balance of Grg tokens in the vault.


Return values:

| Name | Type    | Description     |
| :--- | :------ | :-------------- |
| [0]  | uint256 | Balance in Grg. |
