# IStakingProxy

## Overview

#### License: Apache 2.0

```solidity
interface IStakingProxy
```


## Events info

### StakingContractAttachedToProxy

```solidity
event StakingContractAttachedToProxy(address newStakingContractAddress)
```

Emitted by StakingProxy when a staking contract is attached.


Parameters:

| Name                      | Type    | Description                                 |
| :------------------------ | :------ | :------------------------------------------ |
| newStakingContractAddress | address | Address of newly attached staking contract. |

### StakingContractDetachedFromProxy

```solidity
event StakingContractDetachedFromProxy()
```

Emitted by StakingProxy when a staking contract is detached.
## Functions info

### attachStakingContract (0x66615d56)

```solidity
function attachStakingContract(address stakingImplementation) external
```

Attach a staking contract; future calls will be delegated to the staking contract.

Note that this is callable only by an authorized address.


Parameters:

| Name                  | Type    | Description                  |
| :-------------------- | :------ | :--------------------------- |
| stakingImplementation | address | Address of staking contract. |

### detachStakingContract (0x37b006a6)

```solidity
function detachStakingContract() external
```

Detach the current staking contract.

Note that this is callable only by an authorized address.
### batchExecute (0x856a65eb)

```solidity
function batchExecute(
    bytes[] calldata data
) external returns (bytes[] memory batchReturnData)
```

Batch executes a series of calls to the staking contract.


Parameters:

| Name | Type    | Description                                                                             |
| :--- | :------ | :-------------------------------------------------------------------------------------- |
| data | bytes[] | An array of data that encodes a sequence of functions to call in the staking contracts. |

### assertValidStorageParams (0xc6f3a427)

```solidity
function assertValidStorageParams() external view
```

Asserts initialziation parameters are correct.

Asserts that an epoch is between 5 and 30 days long.

Asserts that 0 < cobb douglas alpha value <= 1.

Asserts that a stake weight is <= 100%.

Asserts that pools allow >= 1 maker.

Asserts that all addresses are initialized.