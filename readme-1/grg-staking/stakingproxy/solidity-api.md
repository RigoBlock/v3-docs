# Solidity API

## StakingProxy

\#dev The RigoBlock Staking contract.

### constructor

```solidity
constructor(address stakingImplementation, address newOwner) public
```

Constructor.

#### Parameters

| Name                  | Type    | Description                                           |
| --------------------- | ------- | ----------------------------------------------------- |
| stakingImplementation | address | Address of the staking contract to delegate calls to. |
| newOwner              | address | Address of the staking proxy owner.                   |

### fallback

```solidity
fallback() external
```

Delegates calls to the staking contract, if it is set.

### attachStakingContract

```solidity
function attachStakingContract(address stakingImplementation) external
```

Attach a staking contract; future calls will be delegated to the staking contract.

_Note that this is callable only by an authorized address._

#### Parameters

| Name                  | Type    | Description                  |
| --------------------- | ------- | ---------------------------- |
| stakingImplementation | address | Address of staking contract. |

### detachStakingContract

```solidity
function detachStakingContract() external
```

Detach the current staking contract.

_Note that this is callable only by an authorized address._

### batchExecute

```solidity
function batchExecute(bytes[] data) external returns (bytes[] batchReturnData)
```

Batch executes a series of calls to the staking contract.

#### Parameters

| Name | Type     | Description                                                                             |
| ---- | -------- | --------------------------------------------------------------------------------------- |
| data | bytes\[] | An array of data that encodes a sequence of functions to call in the staking contracts. |

### assertValidStorageParams

```solidity
function assertValidStorageParams() public view
```

Asserts initialziation parameters are correct.

_Asserts that an epoch is between 5 and 30 days long. Asserts that 0 < cobb douglas alpha value <= 1. Asserts that a stake weight is <= 100%. Asserts that pools allow >= 1 maker. Asserts that all addresses are initialized._

### \_attachStakingContract

```solidity
function _attachStakingContract(address stakingImplementation) internal
```

_Attach a staking contract; future calls will be delegated to the staking contract._

#### Parameters

| Name                  | Type    | Description                  |
| --------------------- | ------- | ---------------------------- |
| stakingImplementation | address | Address of staking contract. |
