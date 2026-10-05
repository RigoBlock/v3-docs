# StakingProxy

## Overview

#### License: Apache 2.0

```solidity
contract StakingProxy is IStakingProxy, MixinStorage, MixinConstants
```

#dev The RigoBlock Staking contract.
## Functions info

### constructor

```solidity
constructor(
    address stakingImplementation,
    address newOwner
) Authorizable(newOwner) MixinStorage()
```

Constructor.


Parameters:

| Name                  | Type    | Description                                            |
| :-------------------- | :------ | :----------------------------------------------------- |
| stakingImplementation | address | Address of the staking contract to delegate calls to.  |
| newOwner              | address | Address of the staking proxy owner.                    |

### fallback

```solidity
fallback() external
```

Delegates calls to the staking contract, if it is set.
### attachStakingContract (0x66615d56)

```solidity
function attachStakingContract(
    address stakingImplementation
) external override onlyAuthorized
```

Attach a staking contract; future calls will be delegated to the staking contract.

Note that this is callable only by an authorized address.


Parameters:

| Name                  | Type    | Description                  |
| :-------------------- | :------ | :--------------------------- |
| stakingImplementation | address | Address of staking contract. |

### detachStakingContract (0x37b006a6)

```solidity
function detachStakingContract() external override onlyAuthorized
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
function assertValidStorageParams() public view override
```

Asserts initialziation parameters are correct.

Asserts that an epoch is between 5 and 30 days long.

Asserts that 0 < cobb douglas alpha value <= 1.

Asserts that a stake weight is <= 100%.

Asserts that pools allow >= 1 maker.

Asserts that all addresses are initialized.