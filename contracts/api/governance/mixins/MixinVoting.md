# MixinVoting

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinVoting is MixinState
```

Inherits `MixinState` (which inherits OZ `Governor`) as a single chain, avoiding a
diamond between the voting and state mixins over the Governor branch.
## Errors info

### GovLowVotingPower

```solidity
error GovLowVotingPower(uint256 votingPower, uint256 proposalThreshold)
```

Thrown when the proposer has insufficient voting power.


Parameters:

| Name              | Type    | Description                                   |
| :---------------- | :------ | :-------------------------------------------- |
| votingPower       | uint256 | The proposer's current voting power.          |
| proposalThreshold | uint256 | The minimum voting power required to propose. |

### GovNoActions

```solidity
error GovNoActions()
```

Thrown when a proposal contains no actions.
### GovTooManyActions

```solidity
error GovTooManyActions(uint256 provided, uint256 max)
```

Thrown when a proposal contains too many actions.


Parameters:

| Name     | Type    | Description                                         |
| :------- | :------ | :-------------------------------------------------- |
| provided | uint256 | The number of actions submitted.                    |
| max      | uint256 | The maximum number of actions allowed per proposal. |

### GovVotingClosed

```solidity
error GovVotingClosed(uint256 proposalId, ProposalStatus state)
```

Thrown when a vote is cast outside the active voting period.


Parameters:

| Name       | Type                | Description                        |
| :--------- | :------------------ | :--------------------------------- |
| proposalId | uint256             | The id of the proposal.            |
| state      | enum ProposalStatus | The current state of the proposal. |

### GovAlreadyVoted

```solidity
error GovAlreadyVoted(uint256 proposalId, address voter)
```

Thrown when a voter tries to vote twice on the same proposal.


Parameters:

| Name       | Type    | Description                         |
| :--------- | :------ | :---------------------------------- |
| proposalId | uint256 | The id of the proposal.             |
| voter      | address | The address that has already voted. |

### GovNoVotes

```solidity
error GovNoVotes(address voter)
```

Thrown when a voter has no voting power.


Parameters:

| Name  | Type    | Description                         |
| :---- | :------ | :---------------------------------- |
| voter | address | The address that attempted to vote. |

### GovExecutionValueMismatch

```solidity
error GovExecutionValueMismatch(uint256 required, uint256 provided)
```

Thrown when `execute` is called with insufficient native tokens.


Parameters:

| Name     | Type    | Description                                     |
| :------- | :------ | :---------------------------------------------- |
| required | uint256 | The amount required for execution.              |
| provided | uint256 | The amount of native tokens sent with the call. |

### GovUnableToCancel

```solidity
error GovUnableToCancel(uint256 proposalId, address caller)
```

Thrown when an account other than the proposer tries to cancel a proposal.


Parameters:

| Name       | Type    | Description                                  |
| :--------- | :------ | :------------------------------------------- |
| proposalId | uint256 | The id of the proposal.                      |
| caller     | address | The account that attempted the cancellation. |

### GovActionsLengthMismatch

```solidity
error GovActionsLengthMismatch()
```

Thrown when the OZ-format propose receives arrays of different lengths.
### GovInvalidSupport

```solidity
error GovInvalidSupport(uint8 support)
```

Thrown when a vote is cast with a support value that is not a valid vote type.


Parameters:

| Name    | Type  | Description                 |
| :------ | :---- | :-------------------------- |
| support | uint8 | The supplied support value. |

### GovProposalIdUnknown

```solidity
error GovProposalIdUnknown(bytes32 proposalHash)
```

Thrown when the OZ-format execute does not match any stored proposal.


Parameters:

| Name         | Type    | Description                                                          |
| :----------- | :------ | :------------------------------------------------------------------- |
| proposalHash | bytes32 | The OpenZeppelin proposal hash computed from the supplied arguments. |

## Functions info

### propose (0x367015bb)

```solidity
function propose(
    IGovernanceVoting.ProposedAction[] memory actions,
    string memory description
) external override returns (uint256 proposalId)
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

### propose (0x7d5e81e2)

```solidity
function propose(
    address[] memory targets,
    uint256[] memory values,
    bytes[] memory calldatas,
    string memory description
) public override returns (uint256 proposalId)
```

Must not call super: OZ Governor linear storage (slots 0-6) must stay empty. See docs/governance/TALLY_COMPAT.md.
Create a new proposal. Vote starts after a delay specified by {IGovernor-votingDelay} and lasts for a
duration specified by {IGovernor-votingPeriod}.

Emits a {ProposalCreated} event.

NOTE: The state of the Governor and `targets` may change between the proposal creation and its execution.
This may be the result of third party actions on the targeted contracts, or other governor proposals.
For example, the balance of this contract could be updated or its access control permissions may be modified,
possibly compromising the proposal's ability to execute successfully (e.g. the governor doesn't have enough
value to cover a proposal with multiple transfers).
### nonces (0x7ecebe00)

```solidity
function nonces(address owner) public view override returns (uint256)
```

Voter nonces are tracked in an ERC-7201 slot (see `_voterNonces`) instead of OZ
`Nonces`'s private regular mapping, keeping all live governance state namespaced.
### execute (0xfe0d94c1)

```solidity
function execute(uint256 proposalId) external payable override
```

Executes a proposal that has passed and is currently executable.


Parameters:

| Name       | Type    | Description                        |
| :--------- | :------ | :--------------------------------- |
| proposalId | uint256 | The ID of the proposal to execute. |

### execute (0x2656227d)

```solidity
function execute(
    address[] memory targets,
    uint256[] memory values,
    bytes[] memory calldatas,
    bytes32 descriptionHash
) public payable override returns (uint256 proposalId)
```

Must not call super: OZ Governor linear storage (slots 0-6) must stay empty. See docs/governance/TALLY_COMPAT.md.
Execute a successful proposal. This requires the quorum to be reached, the vote to be successful, and the
deadline to be reached. Depending on the governor it might also be required that the proposal was queued and
that some delay passed.

Emits a {ProposalExecuted} event.

NOTE: Some modules can modify the requirements for execution, for example by adding an additional timelock.
### cancel (0x40e58ee5)

```solidity
function cancel(uint256 proposalId) external override
```

Cancels a proposal that has not started voting yet.

Only the proposer can cancel, and only while the proposal is Pending. A canceled
proposal cannot be voted on or executed. Cancelling does not consume the proposal id.


Parameters:

| Name       | Type    | Description                       |
| :--------- | :------ | :-------------------------------- |
| proposalId | uint256 | The ID of the proposal to cancel. |

### cancel (0x452115d6)

```solidity
function cancel(
    address[] memory targets,
    uint256[] memory values,
    bytes[] memory calldatas,
    bytes32 descriptionHash
) public override returns (uint256 proposalId)
```

Must not call super: OZ Governor linear storage (slots 0-6) must stay empty. See docs/governance/TALLY_COMPAT.md.
Cancel a proposal. A proposal is cancellable by the proposer, but only while it is Pending state, i.e.
before the vote starts.

Emits a {ProposalCanceled} event.