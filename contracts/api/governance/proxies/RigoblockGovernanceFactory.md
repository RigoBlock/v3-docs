# RigoblockGovernanceFactory

## Overview

#### License: Apache-2.0-or-later

```solidity
contract RigoblockGovernanceFactory is IRigoblockGovernanceFactory
```


## Functions info

### createGovernance (0xa1cbaff4)

```solidity
function createGovernance(
    address implementation,
    address governanceStrategy,
    uint256 proposalThreshold,
    uint256 quorumThreshold,
    TimeType timeType,
    string calldata name
) external returns (address governance)
```

Creates a new governance proxy.


Parameters:

| Name               | Type          | Description                                            |
| :----------------- | :------------ | :----------------------------------------------------- |
| implementation     | address       | Address of the governance implementation contract.     |
| governanceStrategy | address       | Address of the voting strategy.                        |
| proposalThreshold  | uint256       | Number of votes required for creating a new proposal.  |
| quorumThreshold    | uint256       | Number of votes required for execution.                |
| timeType           | enum TimeType | Enum of time type (block number or timestamp).         |
| name               | string        | Human readable string of the name.                     |


Return values:

| Name       | Type    | Description                    |
| :--------- | :------ | :----------------------------- |
| governance | address | Address of the new governance. |

### parameters (0x89035730)

```solidity
function parameters()
    external
    view
    override
    returns (IRigoblockGovernanceFactory.Parameters memory)
```

Returns the governance initialization parameters at proxy deploy.


Return values:

| Name | Type                                          | Description                         |
| :--- | :-------------------------------------------- | :---------------------------------- |
| [0]  | struct IRigoblockGovernanceFactory.Parameters | Tuple of the governance parameters. |
