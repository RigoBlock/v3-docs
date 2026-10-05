# MixinState

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinState is Governor, MixinStorage, MixinAbstract
```


## Functions info

### getActions (0x328dd982)

```solidity
function getActions(
    uint256 proposalId
)
    external
    view
    override
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

### getProposalState (0x9080936f)

```solidity
function getProposalState(
    uint256 proposalId
) external view override returns (ProposalStatus)
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
) external view override returns (IGovernanceState.Receipt memory)
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
) external view override returns (uint256)
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
    override
    returns (IGovernanceState.EnhancedParams memory)
```

Returns the governance parameters.


Return values:

| Name | Type                                   | Description                         |
| :--- | :------------------------------------- | :---------------------------------- |
| [0]  | struct IGovernanceState.EnhancedParams | Tuple of the governance parameters. |

### name (0x06fdde03)

```solidity
function name() public view override returns (string memory)
```

module:core

Name of the governor instance (used in building the EIP-712 domain separator).
### proposalCount (0xda35c664)

```solidity
function proposalCount() external view override returns (uint256 count)
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
    override
    returns (IGovernanceState.ProposalWrapper[] memory proposalWrapper)
```

Returns all proposals ever made to the governance.


Return values:

| Name            | Type                                      | Description                              |
| :-------------- | :---------------------------------------- | :--------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper[] | Tuple array of all governance proposals. |

### votingPeriod (0x02a251a3)

```solidity
function votingPeriod() public view override returns (uint256)
```

module:user-config

Delay between the vote start and vote end. The unit this duration is expressed in depends on the clock
(see ERC-6372) this contract uses.

NOTE: The {votingDelay} can delay the start of the vote. This must be considered when setting the voting
duration compared to the voting delay.

NOTE: This value is stored when the proposal is submitted so that possible changes to the value do not affect
proposals that have already been submitted. The type used to save it is a uint32. Consequently, while this
interface returns a uint256, the value it returns should fit in a uint32.
### CLOCK_MODE (0x4bf5d7e9)

```solidity
function CLOCK_MODE() public pure override returns (string memory)
```

Description of the clock
### clock (0x91ddadf4)

```solidity
function clock() public view override returns (uint48)
```

Clock used for flagging checkpoints. Can be overridden to implement timestamp based checkpoints (and voting).

NOTE: Clock must not return 0.
### supportsInterface (0x01ffc9a7)

```solidity
function supportsInterface(
    bytes4 interfaceId
) public view override returns (bool)
```

Returns true if this contract implements the interface defined by
`interfaceId`. See the corresponding
https://eips.ethereum.org/EIPS/eip-165#how-interfaces-are-identified[ERC section]
to learn more about how these ids are created.

This function call must use less than 30 000 gas.
### COUNTING_MODE (0xdd4e2ba5)

```solidity
function COUNTING_MODE() public pure override returns (string memory)
```

module:voting

A description of the possible `support` values for {castVote} and the way these votes are counted, meant to
be consumed by UIs to show correct vote options and interpret the results. The string is a URL-encoded sequence of
key-value pairs that each describe one aspect, for example `support=bravo&quorum=for,abstain`.

There are 2 standard keys: `support` and `quorum`.

- `support=bravo` refers to the vote options 0 = Against, 1 = For, 2 = Abstain, as in `GovernorBravo`.
- `quorum=bravo` means that only For votes are counted towards quorum.
- `quorum=for,abstain` means that both For and Abstain votes are counted towards quorum.

If a counting module makes use of encoded `params`, it should  include this under a `params` key with a unique
name that describes the behavior. For example:

- `params=fractional` might refer to a scheme where votes are divided fractionally between for/against/abstain.
- `params=erc721` might refer to a scheme where specific NFTs are delegated to vote.

NOTE: The string can be decoded by the standard
https://developer.mozilla.org/en-US/docs/Web/API/URLSearchParams[`URLSearchParams`]
JavaScript class.
### hashProposal (0xc59057e4)

```solidity
function hashProposal(
    address[] memory targets,
    uint256[] memory values,
    bytes[] memory calldatas,
    bytes32 descriptionHash
) public pure override returns (uint256)
```

module:core

Hashing function used to (re)build the proposal id from the proposal details.

NOTE: For all off-chain and external calls, use {getProposalId}.
### getProposalId (0xa8f8a668)

```solidity
function getProposalId(
    address[] memory targets,
    uint256[] memory values,
    bytes[] memory calldatas,
    bytes32 descriptionHash
) public view override returns (uint256)
```

module:core

Function used to get the proposal id from the proposal details.
### proposalProposer (0x143489d0)

```solidity
function proposalProposer(
    uint256 proposalId
) public view override returns (address)
```

module:core

The account that created a proposal.
### proposalEta (0xab58fb8e)

```solidity
function proposalEta(uint256) public pure override returns (uint256)
```

module:core

eta is the timelock availability timestamp, written by `queue()`. With no
timelock nothing is ever queued, so it is always 0; returning the voting
deadline here would flip OZ `state()` from Succeeded to Queued.
The time when a queued proposal becomes executable ("ETA"). Unlike {proposalSnapshot} and
{proposalDeadline}, this doesn't use the governor clock, and instead relies on the executor's clock which may be
different. In most cases this will be a timestamp.
### proposalNeedsQueuing (0xa9a95294)

```solidity
function proposalNeedsQueuing(uint256) public pure override returns (bool)
```

module:core

Whether a proposal needs to be queued before execution.
### state (0x3e4f49e6)

```solidity
function state(
    uint256 proposalId
) public view override returns (IGovernor.ProposalState)
```

module:core

Must not call super: OZ Governor linear storage (slots 0-6) must stay empty. See docs/governance/TALLY_COMPAT.md.
Current state of a proposal, following Compound's convention
### votingDelay (0x3932abb1)

```solidity
function votingDelay() public pure override returns (uint256)
```

module:user-config

Delay, between the proposal is created and the vote starts. The unit this duration is expressed in depends
on the clock (see ERC-6372) this contract uses.

This can be increased to leave time for users to buy voting power, or delegate it, before the voting of a
proposal starts.

NOTE: While this interface returns a uint256, timepoints are stored as uint48 following the ERC-6372 clock type.
Consequently this value must fit in a uint48 (when added to the current clock). See {IERC6372-clock}.
### proposalSnapshot (0x2d63f693)

```solidity
function proposalSnapshot(
    uint256 proposalId
) public view override returns (uint256)
```

module:core

Timepoint used to retrieve user's votes and quorum. If using block number (as per Compound's Comp), the
snapshot is performed at the end of this block. Hence, voting for this proposal starts at the beginning of the
following block.
### proposalDeadline (0xc01f9e37)

```solidity
function proposalDeadline(
    uint256 proposalId
) public view override returns (uint256)
```

module:core

Timepoint at which votes close. If using block number, votes close at the end of this block, so it is
possible to cast a vote during this block.
### proposalThreshold (0xb58131b0)

```solidity
function proposalThreshold() public view override returns (uint256)
```

module:core

The number of votes required in order for a voter to become a proposer.
### quorum (0xf8ce560a)

```solidity
function quorum(uint256) public view override returns (uint256)
```

module:user-config

Minimum number of cast voted required for a proposal to be successful.

NOTE: The `timepoint` parameter corresponds to the snapshot used for counting vote. This allows to scale the
quorum depending on values such as the totalSupply of a token at this timepoint (see {ERC20Votes}).
### hasVoted (0x43859632)

```solidity
function hasVoted(
    uint256 proposalId,
    address account
) public view override returns (bool)
```

module:voting

Returns whether `account` has cast a vote on `proposalId`.
### version (0x54fd4d50)

```solidity
function version() public view override returns (string memory)
```

module:core

Version of the governor instance (used in building the EIP-712 domain separator). Default: "1"
### getProposalById (0x3656de21)

```solidity
function getProposalById(
    uint256 proposalId
)
    public
    view
    override
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
