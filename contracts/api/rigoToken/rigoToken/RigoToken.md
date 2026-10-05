# RigoToken

## Overview

#### License: Apache 2.0

```solidity
contract RigoToken is IRigoToken, UnlimitedAllowanceToken
```

Author: Gabriele Rigo - <gab@rigoblock.com>

UnlimitedAllowanceToken is ERC20
## Constants info

### name (0x06fdde03)

```solidity
string constant name = "Rigo Token"
```


### symbol (0x95d89b41)

```solidity
string constant symbol = "GRG"
```


### decimals (0x313ce567)

```solidity
uint8 constant decimals = 18
```


## State variables info

### minter (0x07546172)

```solidity
address minter
```


### rigoblock (0x3f04d040)

```solidity
address rigoblock
```


## Modifiers info

### onlyMinter

```solidity
modifier onlyMinter()
```


### onlyRigoblock

```solidity
modifier onlyRigoblock()
```


## Functions info

### constructor

```solidity
constructor(address setMinter, address setRigoblock, address grgHolder)
```


### mintToken (0x79c65068)

```solidity
function mintToken(
    address recipient,
    uint256 amount
) external override onlyMinter
```

Allows minter to create new tokens.

Mint method is reserved for minter module.


Parameters:

| Name      | Type    | Description                        |
| :-------- | :------ | :--------------------------------- |
| recipient | address | Address receiving the new tokens.  |
| amount    | uint256 | Number of minted tokens.           |

### changeMintingAddress (0x51892f07)

```solidity
function changeMintingAddress(
    address newAddress
) external override onlyRigoblock
```

Allows Rigoblock Dao to update minter.


Parameters:

| Name       | Type    | Description                |
| :--------- | :------ | :------------------------- |
| newAddress | address | Address of the new minter. |

### changeRigoblockAddress (0x882f7e83)

```solidity
function changeRigoblockAddress(
    address newAddress
) external override onlyRigoblock
```

Allows Rigoblock Dao to update its address.


Parameters:

| Name       | Type    | Description             |
| :--------- | :------ | :---------------------- |
| newAddress | address | Address of the new Dao. |
