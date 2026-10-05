# Inflation

## Overview

#### License: Apache 2.0

```solidity
contract Inflation is IInflation
```

Author: Gabriele Rigo - <gab@rigoblock.com>
## State variables info

### rigoToken (0xd6c1aca7)

```solidity
address immutable rigoToken
```


### stakingProxy (0x22f80d11)

```solidity
address immutable stakingProxy
```


### epochLength (0x57d775f8)

```solidity
uint48 epochLength
```


### slot (0x1a88bc66)

```solidity
uint32 slot
```


## Modifiers info

### onlyStakingProxy

```solidity
modifier onlyStakingProxy()
```


## Functions info

### constructor

```solidity
constructor(address newRigoToken, address newStakingProxy)
```


### mintInflation (0xc551a2f9)

```solidity
function mintInflation()
    external
    override
    onlyStakingProxy
    returns (uint256 mintedInflation)
```

Allows staking proxy to mint rewards.


Return values:

| Name            | Type    | Description                 |
| :-------------- | :------ | :-------------------------- |
| mintedInflation | uint256 | Number of allocated tokens. |

### epochEnded (0x175db3c4)

```solidity
function epochEnded() external view override returns (bool)
```

Returns whether an epoch has ended.


Return values:

| Name | Type | Description               |
| :--- | :--- | :------------------------ |
| [0]  | bool | Bool the epoch has ended. |

### getEpochInflation (0xe9a0bae7)

```solidity
function getEpochInflation() public view override returns (uint256)
```

Returns the epoch inflation.


Return values:

| Name | Type    | Description                               |
| :--- | :------ | :---------------------------------------- |
| [0]  | uint256 | Value of units of GRG minted in an epoch. |

### timeUntilNextClaim (0x6dd73944)

```solidity
function timeUntilNextClaim() external view override returns (uint256)
```

Returns how long until next claim.


Return values:

| Name | Type    | Description        |
| :--- | :------ | :----------------- |
| [0]  | uint256 | Number in seconds. |
