# IRigoToken

## Overview

#### License: Apache 2.0

```solidity
interface IRigoToken is IERC20
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Events info

### TokenMinted

```solidity
event TokenMinted(address indexed recipient, uint256 amount)
```

Emitted when new tokens have been minted.


Parameters:

| Name      | Type    | Description                        |
| :-------- | :------ | :--------------------------------- |
| recipient | address | Address receiving the new tokens.  |
| amount    | uint256 | Number of minted units.            |

## Functions info

### minter (0x07546172)

```solidity
function minter() external view returns (address)
```

Returns the address of the minter.


Return values:

| Name | Type    | Description            |
| :--- | :------ | :--------------------- |
| [0]  | address | Address of the minter. |

### rigoblock (0x3f04d040)

```solidity
function rigoblock() external view returns (address)
```

Returns the address of the Rigoblock Dao.


Return values:

| Name | Type    | Description         |
| :--- | :------ | :------------------ |
| [0]  | address | Address of the Dao. |

### mintToken (0x79c65068)

```solidity
function mintToken(address recipient, uint256 amount) external
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
function changeMintingAddress(address newAddress) external
```

Allows Rigoblock Dao to update minter.


Parameters:

| Name       | Type    | Description                |
| :--------- | :------ | :------------------------- |
| newAddress | address | Address of the new minter. |

### changeRigoblockAddress (0x882f7e83)

```solidity
function changeRigoblockAddress(address newAddress) external
```

Allows Rigoblock Dao to update its address.


Parameters:

| Name       | Type    | Description             |
| :--------- | :------ | :---------------------- |
| newAddress | address | Address of the new Dao. |
