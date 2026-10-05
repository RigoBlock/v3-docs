# IGovernanceState

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceState
```


## Structs info

### Proposal

```solidity
struct Proposal {
	uint256 actionsLength;
	uint256 startBlockOrTime;
	uint256 endBlockOrTime;
	uint256 votesFor;
	uint256 votesAgainst;
	uint256 votesAbstain;
	bool executed;
}
```


### ProposalWrapper

```solidity
struct ProposalWrapper {
	IGovernanceState.Proposal proposal;
	IGovernanceVoting.ProposedAction[] proposedAction;
}
```


### Receipt

```solidity
struct Receipt {
	bool hasVoted;
	uint96 votes;
	IGovernanceVoting.VoteType voteType;
}
```


### GovernanceParameters

```solidity
struct GovernanceParameters {
	address strategy;
	uint256 proposalThreshold;
	uint256 quorumThreshold;
	TimeType timeType;
}
```


### EnhancedParams

```solidity
struct EnhancedParams {
	IGovernanceState.GovernanceParameters params;
	string name;
	string version;
}
```


## Functions info

### getActions (0x328dd982)

```solidity
function getActions(
    uint256 proposalId
)
    external
    view
    returns (IGovernanceVoting.ProposedAction[] memory proposedActions)
```

Returns the actions proposed for a given proposal.


Parameters:

| Name       | Type    | Description              |
| :--------- | :------ | :----------------------- |
| proposalId | uint256 | Number of the proposal.  |


Return values:

| Name            | Type                                      | Description                         |
| :-------------- | :---------------------------------------- | :---------------------------------- |
| proposedActions | struct IGovernanceVoting.ProposedAction[] | Array of tuple of proposed actions. |

### getProposalById (0x3656de21)

```solidity
function getProposalById(
    uint256 proposalId
)
    external
    view
    returns (IGovernanceState.ProposalWrapper memory proposalWrapper)
```

Returns a proposal for a given id.


Parameters:

| Name       | Type    | Description                  |
| :--------- | :------ | :--------------------------- |
| proposalId | uint256 | The number of the proposal.  |


Return values:

| Name            | Type                                    | Description                                                |
| :-------------- | :-------------------------------------- | :--------------------------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper | Tuple wrapper of the proposal and proposed actions tuples. |

### getProposalState (0x9080936f)

```solidity
function getProposalState(
    uint256 proposalId
) external view returns (ProposalStatus)
```

Returns the state of a proposal.


Parameters:

| Name       | Type    | Description              |
| :--------- | :------ | :----------------------- |
| proposalId | uint256 | Number of the proposal.  |


Return values:

| Name | Type                | Description               |
| :--- | :------------------ | :------------------------ |
| [0]  | enum ProposalStatus | Number of proposal state. |

### getReceipt (0xe23a9a52)

```solidity
function getReceipt(
    uint256 proposalId,
    address voter
) external view returns (IGovernanceState.Receipt memory)
```

Returns the receipt of a voter for a given proposal.


Parameters:

| Name       | Type    | Description              |
| :--------- | :------ | :----------------------- |
| proposalId | uint256 | Number of the proposal.  |
| voter      | address | Address of the voter.    |


Return values:

| Name | Type                            | Description             |
| :--- | :------------------------------ | :---------------------- |
| [0]  | struct IGovernanceState.Receipt | Tuple of voter receipt. |

### getVotingPower (0xbb4d4436)

```solidity
function getVotingPower(
    address account
) external view returns (uint256 votingPower)
```

Computes the current voting power of the given account.


Parameters:

| Name    | Type    | Description                  |
| :------ | :------ | :--------------------------- |
| account | address | The address of the account.  |


Return values:

| Name        | Type    | Description                                    |
| :---------- | :------ | :--------------------------------------------- |
| votingPower | uint256 | The current voting power of the given account. |

### governanceParameters (0xa221b74a)

```solidity
function governanceParameters()
    external
    view
    returns (IGovernanceState.EnhancedParams memory)
```

Returns the governance parameters.


Return values:

| Name | Type                                   | Description                         |
| :--- | :------------------------------------- | :---------------------------------- |
| [0]  | struct IGovernanceState.EnhancedParams | Tuple of the governance parameters. |

### proposalCount (0xda35c664)

```solidity
function proposalCount() external view returns (uint256 count)
```

Returns the total number of proposals.


Return values:

| Name  | Type    | Description              |
| :---- | :------ | :----------------------- |
| count | uint256 | The number of proposals. |

### proposals (0x55ef20e6)

```solidity
function proposals()
    external
    view
    returns (IGovernanceState.ProposalWrapper[] memory proposalWrapper)
```

Returns all proposals ever made to the governance.


Return values:

| Name            | Type                                      | Description                              |
| :-------------- | :---------------------------------------- | :--------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper[] | Tuple array of all governance proposals. |
