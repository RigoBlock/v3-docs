# IAGovernance

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IAGovernance
```


## Functions info

### propose (0x367015bb)

```solidity
function propose(
    IGovernanceVoting.ProposedAction[] calldata actions,
    string calldata description
) external returns (uint256 proposalId)
```

Allows to make a proposal to the Rigoblock governance.


Parameters:

| Name        | Type                                      | Description                           |
| :---------- | :---------------------------------------- | :------------------------------------ |
| actions     | struct IGovernanceVoting.ProposedAction[] | Array of tuples of proposed actions.  |
| description | string                                    | A human-readable description.         |


Return values:

| Name       | Type    | Description                           |
| :--------- | :------ | :------------------------------------ |
| proposalId | uint256 | Number of the newly created proposal. |

### castVote (0x56781388)

```solidity
function castVote(uint256 proposalId, uint8 support) external
```

Allows a pool to vote on a proposal.

The support value is passed verbatim to the governance, which interprets it
according to its own VoteType ordering (see docs/governance/TALLY_COMPAT.md).


Parameters:

| Name       | Type    | Description                                              |
| :--------- | :------ | :------------------------------------------------------- |
| proposalId | uint256 | Number of the proposal.                                  |
| support    | uint8   | Encoded vote type (uint8 for OZ selector compatibility). |

### execute (0xfe0d94c1)

```solidity
function execute(uint256 proposalId) external payable
```

Allows a pool to execute a proposal.

Payable to support proposals whose actions carry native value.


Parameters:

| Name       | Type    | Description             |
| :--------- | :------ | :---------------------- |
| proposalId | uint256 | Number of the proposal. |
