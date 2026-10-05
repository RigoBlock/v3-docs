# IGovernanceVoting

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceVoting
```


## Enums info

### VoteType

```solidity
enum VoteType {
	 Against,
	 For,
	 Abstain
}
```


## Structs info

### ProposedAction

```solidity
struct ProposedAction {
	address target;
	bytes data;
	uint256 value;
}
```


## Functions info

### execute (0xfe0d94c1)

```solidity
function execute(uint256 proposalId) external payable
```

Executes a proposal that has passed and is currently executable.


Parameters:

| Name       | Type    | Description                        |
| :--------- | :------ | :--------------------------------- |
| proposalId | uint256 | The ID of the proposal to execute. |

### cancel (0x40e58ee5)

```solidity
function cancel(uint256 proposalId) external
```

Cancels a proposal that has not started voting yet.

Only the proposer can cancel, and only while the proposal is Pending. A canceled
proposal cannot be voted on or executed. Cancelling does not consume the proposal id.


Parameters:

| Name       | Type    | Description                       |
| :--------- | :------ | :-------------------------------- |
| proposalId | uint256 | The ID of the proposal to cancel. |

### propose (0x367015bb)

```solidity
function propose(
    IGovernanceVoting.ProposedAction[] calldata actions,
    string calldata description
) external returns (uint256 proposalId)
```

Creates a proposal on the the given actions. Must have at least `proposalThreshold`.

Must have at least `proposalThreshold` of voting power to call this function.


Parameters:

| Name        | Type                                      | Description                                                 |
| :---------- | :---------------------------------------- | :---------------------------------------------------------- |
| actions     | struct IGovernanceVoting.ProposedAction[] | The proposed actions. An action specifies a contract call.  |
| description | string                                    | A text description for the proposal.                        |


Return values:

| Name       | Type    | Description                           |
| :--------- | :------ | :------------------------------------ |
| proposalId | uint256 | The ID of the newly created proposal. |
