# A0xRouter

## Overview

#### License: Apache-2.0-or-later

```solidity
contract A0xRouter is IA0xRouter, IMinimumVersion, ReentrancyGuardTransient
```

Author: Gabriele Rigo - <gab@rigoblock.com>

See docs/0x/ACTION_ALLOWLIST.md for the validation model and security rationale.
## Modifiers info

### onlyDelegateCall

```solidity
modifier onlyDelegateCall()
```


## Functions info

### constructor

```solidity
constructor(address allowanceHolder, address deployer)
```



Parameters:

| Name            | Type    | Description                                                           |
| :-------------- | :------ | :-------------------------------------------------------------------- |
| allowanceHolder | address | The 0x AllowanceHolder contract address (chain-specific, immutable).  |
| deployer        | address | The 0x Deployer/Registry contract address (same on all chains).       |

### requiredVersion (0x2ea6c3f0)

```solidity
function requiredVersion() external pure override returns (string memory)
```

Returns the minimum implementation version to use an external application.

Adapters must implement it when modifying proxy state or storage.


Return values:

| Name | Type   | Description                              |
| :--- | :----- | :--------------------------------------- |
| [0]  | string | String of the minimum supported version. |

### exec (0x2213bc0b)

```solidity
function exec(
    address operator,
    address token,
    uint256 amount,
    address payable target,
    bytes calldata data
)
    external
    payable
    override
    nonReentrant
    onlyDelegateCall
    returns (bytes memory)
```

Execute a swap via the 0x AllowanceHolder contract.

The calldata is forwarded unmodified to AllowanceHolder after validation.


Parameters:

| Name     | Type            | Description                                                                      |
| :------- | :-------------- | :------------------------------------------------------------------------------- |
| operator | address         | The address authorized to consume the ephemeral allowance. Must equal `target`.  |
| token    | address         | The sell token address.                                                          |
| amount   | uint256         | The sell token amount.                                                           |
| target   | address payable | The 0x Settler contract address that will execute the swap.                      |
| data     | bytes           | The Settler.execute() calldata containing swap instructions.                     |


Return values:

| Name   | Type  | Description                                |
| :----- | :---- | :----------------------------------------- |
| result | bytes | The return data from AllowanceHolder.exec. |
