# IInflation

## Overview

#### License: Apache 2.0

```solidity
interface IInflation
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## Functions info

### rigoToken (0xd6c1aca7)

```solidity
function rigoToken() external view returns (address)
```

Returns the address of the GRG token.


Return values:

| Name | Type    | Description                         |
| :--- | :------ | :---------------------------------- |
| [0]  | address | Address of the Rigo token contract. |

### stakingProxy (0x22f80d11)

```solidity
function stakingProxy() external view returns (address)
```

Returns the address of the GRG staking proxy.


Return values:

| Name | Type    | Description                    |
| :--- | :------ | :----------------------------- |
| [0]  | address | Address of the proxy contract. |

### epochLength (0x57d775f8)

```solidity
function epochLength() external view returns (uint48)
```

Returns the epoch length in seconds.


Return values:

| Name | Type   | Description        |
| :--- | :----- | :----------------- |
| [0]  | uint48 | Number of seconds. |

### slot (0x1a88bc66)

```solidity
function slot() external view returns (uint32)
```

Returns epoch slot.

Increases by one every new epoch.


Return values:

| Name | Type   | Description                  |
| :--- | :----- | :--------------------------- |
| [0]  | uint32 | Number of latest epoch slot. |

### mintInflation (0xc551a2f9)

```solidity
function mintInflation() external returns (uint256 mintedInflation)
```

Allows staking proxy to mint rewards.


Return values:

| Name            | Type    | Description                 |
| :-------------- | :------ | :-------------------------- |
| mintedInflation | uint256 | Number of allocated tokens. |

### epochEnded (0x175db3c4)

```solidity
function epochEnded() external view returns (bool)
```

Returns whether an epoch has ended.


Return values:

| Name | Type | Description               |
| :--- | :--- | :------------------------ |
| [0]  | bool | Bool the epoch has ended. |

### getEpochInflation (0xe9a0bae7)

```solidity
function getEpochInflation() external view returns (uint256)
```

Returns the epoch inflation.


Return values:

| Name | Type    | Description                               |
| :--- | :------ | :---------------------------------------- |
| [0]  | uint256 | Value of units of GRG minted in an epoch. |

### timeUntilNextClaim (0x6dd73944)

```solidity
function timeUntilNextClaim() external view returns (uint256)
```

Returns how long until next claim.


Return values:

| Name | Type    | Description        |
| :--- | :------ | :----------------- |
| [0]  | uint256 | Number in seconds. |
