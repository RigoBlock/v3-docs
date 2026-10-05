# Staking

## Overview

#### License: Apache 2.0

```solidity
contract Staking is IStaking, MixinParams, MixinStake, MixinPopRewards
```


## Functions info

### constructor

```solidity
constructor(
    address grgVault,
    address poolRegistry,
    address rigoToken
)
    Authorizable(address(0))
    MixinDeploymentConstants(grgVault, poolRegistry, rigoToken)
```

Setting owner to null address prevents admin direct calls to implementation.

Initializing immutable implementation address is used to allow delegatecalls only.

Direct calls to the  implementation contract are effectively locked.


Parameters:

| Name         | Type    | Description                              |
| :----------- | :------ | :--------------------------------------- |
| grgVault     | address | Address of the Grg vault.                |
| poolRegistry | address | Address of the RigoBlock pool registry.  |
| rigoToken    | address | Address of the Grg token.                |

### init (0xe1c7392a)

```solidity
function init() public override onlyAuthorized
```

Initialize storage owned by this contract.

This function should not be called directly.

The StakingProxy contract will call it in `attachStakingContract()`.