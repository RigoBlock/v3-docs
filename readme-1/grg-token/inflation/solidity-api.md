# Solidity API

## Inflation

### rigoToken

```solidity
address rigoToken
```

Returns the address of the GRG token.

#### Return Values

### stakingProxy

```solidity
address stakingProxy
```

Returns the address of the GRG staking proxy.

#### Return Values

### epochLength

```solidity
uint48 epochLength
```

Returns the epoch length in seconds.

#### Return Values

### slot

```solidity
uint32 slot
```

Returns epoch slot.

_Increases by one every new epoch._

#### Return Values

### \_ANNUAL\_INFLATION\_RATE

```solidity
uint32 _ANNUAL_INFLATION_RATE
```

### \_PPM\_DENOMINATOR

```solidity
uint32 _PPM_DENOMINATOR
```

### \_epochEndTime

```solidity
uint48 _epochEndTime
```

### onlyStakingProxy

```solidity
modifier onlyStakingProxy()
```

### constructor

```solidity
constructor(address newRigoToken, address newStakingProxy) public
```

### mintInflation

```solidity
function mintInflation() external returns (uint256 mintedInflation)
```

Allows staking proxy to mint rewards.

#### Return Values

| Name            | Type    | Description                 |
| --------------- | ------- | --------------------------- |
| mintedInflation | uint256 | Number of allocated tokens. |

### epochEnded

```solidity
function epochEnded() external view returns (bool)
```

Returns whether an epoch has ended.

#### Return Values

| Name | Type | Description               |
| ---- | ---- | ------------------------- |
| \[0] | bool | Bool the epoch has ended. |

### getEpochInflation

```solidity
function getEpochInflation() public view returns (uint256)
```

Returns the epoch inflation.

#### Return Values

| Name | Type    | Description                               |
| ---- | ------- | ----------------------------------------- |
| \[0] | uint256 | Value of units of GRG minted in an epoch. |

### timeUntilNextClaim

```solidity
function timeUntilNextClaim() external view returns (uint256)
```

Returns how long until next claim.

#### Return Values

| Name | Type    | Description        |
| ---- | ------- | ------------------ |
| \[0] | uint256 | Number in seconds. |

### \_assertCallerIsStakingProxy

```solidity
function _assertCallerIsStakingProxy() private view
```

_Asserts that the caller is the Staking Proxy._

### \_getEpochEndTime

```solidity
function _getEpochEndTime() private view returns (uint256)
```

### \_getEpochLength

```solidity
function _getEpochLength() private view returns (uint256)
```

### \_getRigoToken

```solidity
function _getRigoToken() private view returns (address)
```

### \_getStakingProxy

```solidity
function _getStakingProxy() private view returns (address)
```
