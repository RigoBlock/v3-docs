# IGovernanceEvents

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceEvents
```


## Events info

### ProposalCreated

```solidity
event ProposalCreated(address proposer, uint256 proposalId, IGovernanceVoting.ProposedAction[] actions, uint256 startBlockOrTime, uint256 endBlockOrTime, string description)
```

Emitted when a new proposal is created.


Parameters:

| Name             | Type                                      | Description                                                 |
| :--------------- | :---------------------------------------- | :---------------------------------------------------------- |
| proposer         | address                                   | Address of the proposer.                                    |
| proposalId       | uint256                                   | Number of the proposal.                                     |
| actions          | struct IGovernanceVoting.ProposedAction[] | Struct array of actions (targets, datas, values).           |
| startBlockOrTime | uint256                                   | Timestamp in seconds after which proposal can be voted on.  |
| endBlockOrTime   | uint256                                   | Timestamp in seconds after which proposal can be executed.  |
| description      | string                                    | String description of proposal.                             |

### StrategyUpgraded

```solidity
event StrategyUpgraded(address newStrategy)
```

Emmited when the governance strategy is upgraded.


Parameters:

| Name        | Type    | Description                           |
| :---------- | :------ | :------------------------------------ |
| newStrategy | address | Address of the new strategy contract. |

### Upgraded

```solidity
event Upgraded(address indexed newImplementation)
```

Emitted when implementation written to proxy storage.

Emitted also at first variable initialization.


Parameters:

| Name              | Type    | Description                        |
| :---------------- | :------ | :--------------------------------- |
| newImplementation | address | Address of the new implementation. |

### VoteCast

```solidity
event VoteCast(address voter, uint256 proposalId, IGovernanceVoting.VoteType voteType, uint256 votingPower)
```

Emitted when a voter votes.


Parameters:

| Name        | Type                            | Description              |
| :---------- | :------------------------------ | :----------------------- |
| voter       | address                         | Address of the voter.    |
| proposalId  | uint256                         | Number of the proposal.  |
| voteType    | enum IGovernanceVoting.VoteType | Number of vote type.     |
| votingPower | uint256                         | Number of votes.         |

### ProposalThresholdSet

```solidity
event ProposalThresholdSet(uint256 proposalThreshold)
```

Emitted when the proposal threshold is updated.


Parameters:

| Name              | Type    | Description                 |
| :---------------- | :------ | :-------------------------- |
| proposalThreshold | uint256 | The new proposal threshold. |
