# Solidity API

## RigoToken

UnlimitedAllowanceToken is ERC20

### name

```solidity
string name
```

### symbol

```solidity
string symbol
```

### decimals

```solidity
uint8 decimals
```

### minter

```solidity
address minter
```

Returns the address of the minter.

#### Return Values

### rigoblock

```solidity
address rigoblock
```

Returns the address of the Rigoblock Dao.

#### Return Values

### onlyMinter

```solidity
modifier onlyMinter()
```

### onlyRigoblock

```solidity
modifier onlyRigoblock()
```

### constructor

```solidity
constructor(address setMinter, address setRigoblock, address grgHolder) public
```

### mintToken

```solidity
function mintToken(address recipient, uint256 amount) external
```

Allows minter to create new tokens.

_Mint method is reserved for minter module._

#### Parameters

| Name      | Type    | Description                       |
| --------- | ------- | --------------------------------- |
| recipient | address | Address receiving the new tokens. |
| amount    | uint256 | Number of minted tokens.          |

### changeMintingAddress

```solidity
function changeMintingAddress(address newAddress) external
```

Allows Rigoblock Dao to update minter.

#### Parameters

| Name       | Type    | Description                |
| ---------- | ------- | -------------------------- |
| newAddress | address | Address of the new minter. |

### changeRigoblockAddress

```solidity
function changeRigoblockAddress(address newAddress) external
```

Allows Rigoblock Dao to update its address.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| newAddress | address | Address of the new Dao. |
