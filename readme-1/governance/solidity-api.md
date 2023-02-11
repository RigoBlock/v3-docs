# Solidity API

## IRigoblockGovernance

## RigoblockGovernance

### constructor

```solidity
constructor() public
```

Constructor has no inputs to guarantee same deterministic address across chains.

_Setting high proposal threshold locks propose action, which also lock vote actions._

## IGovernanceStrategy

### assertValidInitParams

```solidity
function assertValidInitParams(struct IRigoblockGovernanceFactory.Parameters params) external view
```

Reverts if initialization paramters are incorrect.

_Only used at initialization, as params deleted from factory storage after setup._

#### Parameters

| Name   | Type                                          | Description                  |
| ------ | --------------------------------------------- | ---------------------------- |
| params | struct IRigoblockGovernanceFactory.Parameters | Tuple of factory parameters. |

### assertValidThresholds

```solidity
function assertValidThresholds(uint256 proposalThreshold, uint256 quorumThreshold) external view
```

Reverts if thresholds are incorrect.

#### Parameters

| Name              | Type    | Description                                         |
| ----------------- | ------- | --------------------------------------------------- |
| proposalThreshold | uint256 | Number of votes required to make a proposal.        |
| quorumThreshold   | uint256 | Number of votes required for a proposal to succeed. |

### getProposalState

```solidity
function getProposalState(struct IGovernanceState.Proposal proposal, uint256 minimumQuorum) external view returns (enum IGovernanceState.ProposalState)
```

Returns the state of a proposal for a required quorum.

#### Parameters

| Name          | Type                             | Description                                      |
| ------------- | -------------------------------- | ------------------------------------------------ |
| proposal      | struct IGovernanceState.Proposal | Tuple of the proposal.                           |
| minimumQuorum | uint256                          | Number of votes required for a proposal to pass. |

#### Return Values

| Name | Type                                | Description                  |
| ---- | ----------------------------------- | ---------------------------- |
| \[0] | enum IGovernanceState.ProposalState | Tuple of the proposal state. |

### votingPeriod

```solidity
function votingPeriod() external view returns (uint256)
```

Return the voting period.

#### Return Values

| Name | Type    | Description                           |
| ---- | ------- | ------------------------------------- |
| \[0] | uint256 | Number of seconds of period duration. |

### votingTimestamps

```solidity
function votingTimestamps() external view returns (uint256 startBlockOrTime, uint256 endBlockOrTime)
```

Returns the voting timestamps.

#### Return Values

| Name             | Type    | Description                     |
| ---------------- | ------- | ------------------------------- |
| startBlockOrTime | uint256 | Timestamp when proposal starts. |
| endBlockOrTime   | uint256 | Timestamp when voting ends.     |

### getVotingPower

```solidity
function getVotingPower(address account) external view returns (uint256)
```

Return a user's voting power.

#### Parameters

| Name    | Type    | Description                 |
| ------- | ------- | --------------------------- |
| account | address | Address to check votes for. |

## IRigoblockGovernanceFactory

### GovernanceCreated

```solidity
event GovernanceCreated(address governance)
```

Emitted when a governance is created.

#### Parameters

| Name       | Type    | Description                      |
| ---------- | ------- | -------------------------------- |
| governance | address | Address of the governance proxy. |

### createGovernance

```solidity
function createGovernance(address implementation, address governanceStrategy, uint256 proposalThreshold, uint256 quorumThreshold, enum IGovernanceState.TimeType timeType, string name) external returns (address governance)
```

Creates a new governance proxy.

#### Parameters

| Name               | Type                           | Description                                           |
| ------------------ | ------------------------------ | ----------------------------------------------------- |
| implementation     | address                        | Address of the governance implementation contract.    |
| governanceStrategy | address                        | Address of the voting strategy.                       |
| proposalThreshold  | uint256                        | Number of votes required for creating a new proposal. |
| quorumThreshold    | uint256                        | Number of votes required for execution.               |
| timeType           | enum IGovernanceState.TimeType | Enum of time type (block number or timestamp).        |
| name               | string                         | Human readable string of the name.                    |

#### Return Values

| Name       | Type    | Description                    |
| ---------- | ------- | ------------------------------ |
| governance | address | Address of the new governance. |

### Parameters

```solidity
struct Parameters {
  address implementation;
  address governanceStrategy;
  uint256 proposalThreshold;
  uint256 quorumThreshold;
  enum IGovernanceState.TimeType timeType;
  string name;
}
```

### parameters

```solidity
function parameters() external view returns (struct IRigoblockGovernanceFactory.Parameters)
```

Returns the governance initialization parameters at proxy deploy.

#### Return Values

| Name | Type                                          | Description                         |
| ---- | --------------------------------------------- | ----------------------------------- |
| \[0] | struct IRigoblockGovernanceFactory.Parameters | Tuple of the governance parameters. |

## IGovernanceEvents

### ProposalCreated

```solidity
event ProposalCreated(address proposer, uint256 proposalId, struct IGovernanceVoting.ProposedAction[] actions, uint256 startBlockOrTime, uint256 endBlockOrTime, string description)
```

Emitted when a new proposal is created.

#### Parameters

| Name             | Type                                       | Description                                                |
| ---------------- | ------------------------------------------ | ---------------------------------------------------------- |
| proposer         | address                                    | Address of the proposer.                                   |
| proposalId       | uint256                                    | Number of the proposal.                                    |
| actions          | struct IGovernanceVoting.ProposedAction\[] | Struct array of actions (targets, datas, values).          |
| startBlockOrTime | uint256                                    | Timestamp in seconds after which proposal can be voted on. |
| endBlockOrTime   | uint256                                    | Timestamp in seconds after which proposal can be executed. |
| description      | string                                     | String description of proposal.                            |

### ProposalExecuted

```solidity
event ProposalExecuted(uint256 proposalId)
```

Emitted when a proposal is executed.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |

### StrategyUpgraded

```solidity
event StrategyUpgraded(address newStrategy)
```

Emmited when the governance strategy is upgraded.

#### Parameters

| Name        | Type    | Description                           |
| ----------- | ------- | ------------------------------------- |
| newStrategy | address | Address of the new strategy contract. |

### ThresholdsUpdated

```solidity
event ThresholdsUpdated(uint256 proposalThreshold, uint256 quorumThreshold)
```

Emitted when voting thresholds get updated.

_Only governance can update thresholds._

#### Parameters

| Name              | Type    | Description                                     |
| ----------------- | ------- | ----------------------------------------------- |
| proposalThreshold | uint256 | Number of votes required to add a proposal.     |
| quorumThreshold   | uint256 | Number of votes required to execute a proposal. |

### Upgraded

```solidity
event Upgraded(address newImplementation)
```

Emitted when implementation written to proxy storage.

_Emitted also at first variable initialization._

#### Parameters

| Name              | Type    | Description                        |
| ----------------- | ------- | ---------------------------------- |
| newImplementation | address | Address of the new implementation. |

### VoteCast

```solidity
event VoteCast(address voter, uint256 proposalId, enum IGovernanceVoting.VoteType voteType, uint256 votingPower)
```

Emitted when a voter votes.

#### Parameters

| Name        | Type                            | Description             |
| ----------- | ------------------------------- | ----------------------- |
| voter       | address                         | Address of the voter.   |
| proposalId  | uint256                         | Number of the proposal. |
| voteType    | enum IGovernanceVoting.VoteType | Number of vote type.    |
| votingPower | uint256                         | Number of votes.        |

## IGovernanceInitializer

### initializeGovernance

```solidity
function initializeGovernance() external
```

Initializes the Rigoblock Governance.

_Params are stored in factory and read from there._

## IGovernanceState

### ProposalState

```solidity
enum ProposalState {
  Pending,
  Active,
  Canceled,
  Qualified,
  Defeated,
  Succeeded,
  Queued,
  Expired,
  Executed
}
```

### TimeType

```solidity
enum TimeType {
  Blocknumber,
  Timestamp
}
```

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
  struct IGovernanceState.Proposal proposal;
  struct IGovernanceVoting.ProposedAction[] proposedAction;
}
```

### getActions

```solidity
function getActions(uint256 proposalId) external view returns (struct IGovernanceVoting.ProposedAction[] proposedActions)
```

Returns the actions proposed for a given proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |

#### Return Values

| Name            | Type                                       | Description                         |
| --------------- | ------------------------------------------ | ----------------------------------- |
| proposedActions | struct IGovernanceVoting.ProposedAction\[] | Array of tuple of proposed actions. |

### getProposalById

```solidity
function getProposalById(uint256 proposalId) external view returns (struct IGovernanceState.ProposalWrapper proposalWrapper)
```

Returns a proposal for a given id.

#### Parameters

| Name       | Type    | Description                 |
| ---------- | ------- | --------------------------- |
| proposalId | uint256 | The number of the proposal. |

#### Return Values

| Name            | Type                                    | Description                                                |
| --------------- | --------------------------------------- | ---------------------------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper | Tuple wrapper of the proposal and proposed actions tuples. |

### getProposalState

```solidity
function getProposalState(uint256 proposalId) external view returns (enum IGovernanceState.ProposalState)
```

Returns the state of a proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |

#### Return Values

| Name | Type                                | Description               |
| ---- | ----------------------------------- | ------------------------- |
| \[0] | enum IGovernanceState.ProposalState | Number of proposal state. |

### Receipt

```solidity
struct Receipt {
  bool hasVoted;
  uint96 votes;
  enum IGovernanceVoting.VoteType voteType;
}
```

### getReceipt

```solidity
function getReceipt(uint256 proposalId, address voter) external view returns (struct IGovernanceState.Receipt)
```

Returns the receipt of a voter for a given proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |
| voter      | address | Address of the voter.   |

#### Return Values

| Name | Type                            | Description             |
| ---- | ------------------------------- | ----------------------- |
| \[0] | struct IGovernanceState.Receipt | Tuple of voter receipt. |

### getVotingPower

```solidity
function getVotingPower(address account) external view returns (uint256 votingPower)
```

Computes the current voting power of the given account.

#### Parameters

| Name    | Type    | Description                 |
| ------- | ------- | --------------------------- |
| account | address | The address of the account. |

#### Return Values

| Name        | Type    | Description                                    |
| ----------- | ------- | ---------------------------------------------- |
| votingPower | uint256 | The current voting power of the given account. |

### GovernanceParameters

```solidity
struct GovernanceParameters {
  address strategy;
  uint256 proposalThreshold;
  uint256 quorumThreshold;
  enum IGovernanceState.TimeType timeType;
}
```

### EnhancedParams

```solidity
struct EnhancedParams {
  struct IGovernanceState.GovernanceParameters params;
  string name;
  string version;
}
```

### governanceParameters

```solidity
function governanceParameters() external view returns (struct IGovernanceState.EnhancedParams)
```

Returns the governance parameters.

#### Return Values

| Name | Type                                   | Description                         |
| ---- | -------------------------------------- | ----------------------------------- |
| \[0] | struct IGovernanceState.EnhancedParams | Tuple of the governance parameters. |

### name

```solidity
function name() external view returns (string)
```

Returns the name of the governace.

#### Return Values

| Name | Type   | Description                        |
| ---- | ------ | ---------------------------------- |
| \[0] | string | Human readable string of the name. |

### proposalCount

```solidity
function proposalCount() external view returns (uint256 count)
```

Returns the total number of proposals.

#### Return Values

| Name  | Type    | Description              |
| ----- | ------- | ------------------------ |
| count | uint256 | The number of proposals. |

### proposals

```solidity
function proposals() external view returns (struct IGovernanceState.ProposalWrapper[] proposalWrapper)
```

Returns all proposals ever made to the governance.

#### Return Values

| Name            | Type                                       | Description                              |
| --------------- | ------------------------------------------ | ---------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper\[] | Tuple array of all governance proposals. |

### votingPeriod

```solidity
function votingPeriod() external view returns (uint256)
```

Returns the voting period.

#### Return Values

| Name | Type    | Description                  |
| ---- | ------- | ---------------------------- |
| \[0] | uint256 | Number of blocks or seconds. |

## IGovernanceUpgrade

### updateThresholds

```solidity
function updateThresholds(uint256 newProposalThreshold, uint256 newQuorumThreshold) external
```

Updates the proposal and quorum thresholds to the given values.

_Only callable by the governance contract itself. Thresholds can only be updated via a successful governance proposal._

#### Parameters

| Name                 | Type    | Description                               |
| -------------------- | ------- | ----------------------------------------- |
| newProposalThreshold | uint256 | The new value for the proposal threshold. |
| newQuorumThreshold   | uint256 | The new value for the quorum threshold.   |

### upgradeImplementation

```solidity
function upgradeImplementation(address newImplementation) external
```

Updates the governance implementation address.

_Only callable after successful voting._

#### Parameters

| Name              | Type    | Description                                            |
| ----------------- | ------- | ------------------------------------------------------ |
| newImplementation | address | Address of the new governance implementation contract. |

### upgradeStrategy

```solidity
function upgradeStrategy(address newStrategy) external
```

Updates the governance strategy plugin.

_Only callable by the governance contract itself._

#### Parameters

| Name        | Type    | Description                           |
| ----------- | ------- | ------------------------------------- |
| newStrategy | address | Address of the new strategy contract. |

## IGovernanceVoting

### VoteType

```solidity
enum VoteType {
  For,
  Against,
  Abstain
}
```

### castVote

```solidity
function castVote(uint256 proposalId, enum IGovernanceVoting.VoteType voteType) external
```

Casts a vote for the given proposal.

_Only callable during the voting period for that proposal. One address can only vote once._

#### Parameters

| Name       | Type                            | Description                                 |
| ---------- | ------------------------------- | ------------------------------------------- |
| proposalId | uint256                         | The ID of the proposal to vote on.          |
| voteType   | enum IGovernanceVoting.VoteType | Whether to support, not support or abstain. |

### castVoteBySignature

```solidity
function castVoteBySignature(uint256 proposalId, enum IGovernanceVoting.VoteType voteType, uint8 v, bytes32 r, bytes32 s) external
```

Casts a vote for the given proposal, by signature.

_Only callable during the voting period for that proposal. One voter can only vote once._

#### Parameters

| Name       | Type                            | Description                                 |
| ---------- | ------------------------------- | ------------------------------------------- |
| proposalId | uint256                         | The ID of the proposal to vote on.          |
| voteType   | enum IGovernanceVoting.VoteType | Whether to support, not support or abstain. |
| v          | uint8                           | the v field of the signature.               |
| r          | bytes32                         | the r field of the signature.               |
| s          | bytes32                         | the s field of the signature.               |

### execute

```solidity
function execute(uint256 proposalId) external payable
```

Executes a proposal that has passed and is currently executable.

#### Parameters

| Name       | Type    | Description                        |
| ---------- | ------- | ---------------------------------- |
| proposalId | uint256 | The ID of the proposal to execute. |

### ProposedAction

```solidity
struct ProposedAction {
  address target;
  bytes data;
  uint256 value;
}
```

### propose

```solidity
function propose(struct IGovernanceVoting.ProposedAction[] actions, string description) external returns (uint256 proposalId)
```

Creates a proposal on the the given actions. Must have at least `proposalThreshold`.

_Must have at least `proposalThreshold` of voting power to call this function._

#### Parameters

| Name        | Type                                       | Description                                                |
| ----------- | ------------------------------------------ | ---------------------------------------------------------- |
| actions     | struct IGovernanceVoting.ProposedAction\[] | The proposed actions. An action specifies a contract call. |
| description | string                                     | A text description for the proposal.                       |

#### Return Values

| Name       | Type    | Description                           |
| ---------- | ------- | ------------------------------------- |
| proposalId | uint256 | The ID of the newly created proposal. |

## MixinAbstract

### \_getProposalCount

```solidity
function _getProposalCount() internal view virtual returns (uint256)
```

### \_getProposalState

```solidity
function _getProposalState(uint256 proposalId) internal view virtual returns (enum IGovernanceState.ProposalState)
```

### \_getVotingPower

```solidity
function _getVotingPower(address account) internal view virtual returns (uint256)
```

## MixinConstants

Constants are copied in the bytecode and not assigned a storage slot, can safely be added to this contract.

### VERSION

```solidity
string VERSION
```

Contract version

### PROPOSAL\_MAX\_OPERATIONS

```solidity
uint256 PROPOSAL_MAX_OPERATIONS
```

Maximum operations per proposal

### DOMAIN\_TYPEHASH

```solidity
bytes32 DOMAIN_TYPEHASH
```

The EIP-712 typehash for the contract's domain

### VOTE\_TYPEHASH

```solidity
bytes32 VOTE_TYPEHASH
```

The EIP-712 typehash for the vote struct

### \_GOVERNANCE\_PARAMS\_SLOT

```solidity
bytes32 _GOVERNANCE_PARAMS_SLOT
```

### \_IMPLEMENTATION\_SLOT

```solidity
bytes32 _IMPLEMENTATION_SLOT
```

### \_NAME\_SLOT

```solidity
bytes32 _NAME_SLOT
```

### \_PROPOSAL\_SLOT

```solidity
bytes32 _PROPOSAL_SLOT
```

### \_PROPOSAL\_COUNT\_SLOT

```solidity
bytes32 _PROPOSAL_COUNT_SLOT
```

### \_PROPOSED\_ACTION\_SLOT

```solidity
bytes32 _PROPOSED_ACTION_SLOT
```

### \_RECEIPT\_SLOT

```solidity
bytes32 _RECEIPT_SLOT
```

## MixinImmutables

Immutables are copied in the bytecode and not assigned a storage slot

_New immutables can safely be added to this contract without ordering._

### constructor

```solidity
constructor() internal
```

## MixinInitializer

### onlyUninitialized

```solidity
modifier onlyUninitialized()
```

### initializeGovernance

```solidity
function initializeGovernance() external
```

Initializes the Rigoblock Governance.

_Params are stored in factory and read from there._

## MixinState

### getActions

```solidity
function getActions(uint256 proposalId) external view returns (struct IGovernanceVoting.ProposedAction[] proposedActions)
```

Returns the actions proposed for a given proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |

#### Return Values

| Name            | Type                                       | Description                         |
| --------------- | ------------------------------------------ | ----------------------------------- |
| proposedActions | struct IGovernanceVoting.ProposedAction\[] | Array of tuple of proposed actions. |

### getProposalState

```solidity
function getProposalState(uint256 proposalId) external view returns (enum IGovernanceState.ProposalState)
```

Returns the state of a proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |

#### Return Values

| Name | Type                                | Description               |
| ---- | ----------------------------------- | ------------------------- |
| \[0] | enum IGovernanceState.ProposalState | Number of proposal state. |

### getReceipt

```solidity
function getReceipt(uint256 proposalId, address voter) external view returns (struct IGovernanceState.Receipt)
```

Returns the receipt of a voter for a given proposal.

#### Parameters

| Name       | Type    | Description             |
| ---------- | ------- | ----------------------- |
| proposalId | uint256 | Number of the proposal. |
| voter      | address | Address of the voter.   |

#### Return Values

| Name | Type                            | Description             |
| ---- | ------------------------------- | ----------------------- |
| \[0] | struct IGovernanceState.Receipt | Tuple of voter receipt. |

### getVotingPower

```solidity
function getVotingPower(address account) external view returns (uint256)
```

Computes the current voting power of the given account.

#### Parameters

| Name    | Type    | Description                 |
| ------- | ------- | --------------------------- |
| account | address | The address of the account. |

#### Return Values

| Name | Type    | Description |
| ---- | ------- | ----------- |
| \[0] | uint256 |             |

### governanceParameters

```solidity
function governanceParameters() external view returns (struct IGovernanceState.EnhancedParams)
```

Returns the governance parameters.

#### Return Values

| Name | Type                                   | Description                         |
| ---- | -------------------------------------- | ----------------------------------- |
| \[0] | struct IGovernanceState.EnhancedParams | Tuple of the governance parameters. |

### name

```solidity
function name() external view returns (string)
```

Returns the name of the governace.

#### Return Values

| Name | Type   | Description                        |
| ---- | ------ | ---------------------------------- |
| \[0] | string | Human readable string of the name. |

### proposalCount

```solidity
function proposalCount() external view returns (uint256 count)
```

Returns the total number of proposals.

#### Return Values

| Name  | Type    | Description              |
| ----- | ------- | ------------------------ |
| count | uint256 | The number of proposals. |

### proposals

```solidity
function proposals() external view returns (struct IGovernanceState.ProposalWrapper[] proposalWrapper)
```

Returns all proposals ever made to the governance.

#### Return Values

| Name            | Type                                       | Description                              |
| --------------- | ------------------------------------------ | ---------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper\[] | Tuple array of all governance proposals. |

### votingPeriod

```solidity
function votingPeriod() external view returns (uint256)
```

Returns the voting period.

#### Return Values

| Name | Type    | Description                  |
| ---- | ------- | ---------------------------- |
| \[0] | uint256 | Number of blocks or seconds. |

### getProposalById

```solidity
function getProposalById(uint256 proposalId) public view returns (struct IGovernanceState.ProposalWrapper proposalWrapper)
```

Returns a proposal for a given id.

#### Parameters

| Name       | Type    | Description                 |
| ---------- | ------- | --------------------------- |
| proposalId | uint256 | The number of the proposal. |

#### Return Values

| Name            | Type                                    | Description                                                |
| --------------- | --------------------------------------- | ---------------------------------------------------------- |
| proposalWrapper | struct IGovernanceState.ProposalWrapper | Tuple wrapper of the proposal and proposed actions tuples. |

### \_getProposalCount

```solidity
function _getProposalCount() internal view returns (uint256 count)
```

### \_getProposalState

```solidity
function _getProposalState(uint256 proposalId) internal view returns (enum IGovernanceState.ProposalState)
```

### \_getVotingPower

```solidity
function _getVotingPower(address account) internal view returns (uint256)
```

## MixinStorage

### constructor

```solidity
constructor() internal
```

### \_governanceParameters

```solidity
function _governanceParameters() internal pure returns (struct IGovernanceState.GovernanceParameters s)
```

### AddressSlot

```solidity
struct AddressSlot {
  address value;
}
```

### \_implementation

```solidity
function _implementation() internal pure returns (struct MixinStorage.AddressSlot s)
```

### StringSlot

```solidity
struct StringSlot {
  string value;
}
```

### \_name

```solidity
function _name() internal pure returns (struct MixinStorage.StringSlot s)
```

### ParamsWrapper

```solidity
struct ParamsWrapper {
  struct IGovernanceState.GovernanceParameters governanceParameters;
}
```

### \_paramsWrapper

```solidity
function _paramsWrapper() internal pure returns (struct MixinStorage.ParamsWrapper s)
```

### UintSlot

```solidity
struct UintSlot {
  uint256 value;
}
```

### \_proposalCount

```solidity
function _proposalCount() internal pure returns (struct MixinStorage.UintSlot s)
```

### ProposalByIndex

```solidity
struct ProposalByIndex {
  mapping(uint256 => struct IGovernanceState.Proposal) proposalById;
}
```

### \_proposal

```solidity
function _proposal() internal pure returns (struct MixinStorage.ProposalByIndex s)
```

### ActionByIndex

```solidity
struct ActionByIndex {
  mapping(uint256 => mapping(uint256 => struct IGovernanceVoting.ProposedAction)) proposedActionbyIndex;
}
```

### \_proposedAction

```solidity
function _proposedAction() internal pure returns (struct MixinStorage.ActionByIndex s)
```

### UserReceipt

```solidity
struct UserReceipt {
  mapping(uint256 => mapping(address => struct IGovernanceState.Receipt)) userReceiptByProposal;
}
```

### \_receipt

```solidity
function _receipt() internal pure returns (struct MixinStorage.UserReceipt s)
```

## MixinUpgrade

### onlyGovernance

```solidity
modifier onlyGovernance()
```

### updateThresholds

```solidity
function updateThresholds(uint256 newProposalThreshold, uint256 newQuorumThreshold) external
```

Updates the proposal and quorum thresholds to the given values.

_Only callable by the governance contract itself. Thresholds can only be updated via a successful governance proposal._

#### Parameters

| Name                 | Type    | Description                               |
| -------------------- | ------- | ----------------------------------------- |
| newProposalThreshold | uint256 | The new value for the proposal threshold. |
| newQuorumThreshold   | uint256 | The new value for the quorum threshold.   |

### upgradeImplementation

```solidity
function upgradeImplementation(address newImplementation) external
```

Updates the governance implementation address.

_Only callable after successful voting._

#### Parameters

| Name              | Type    | Description                                            |
| ----------------- | ------- | ------------------------------------------------------ |
| newImplementation | address | Address of the new governance implementation contract. |

### upgradeStrategy

```solidity
function upgradeStrategy(address newStrategy) external
```

Updates the governance strategy plugin.

_Only callable by the governance contract itself._

#### Parameters

| Name        | Type    | Description                           |
| ----------- | ------- | ------------------------------------- |
| newStrategy | address | Address of the new strategy contract. |

### \_isContract

```solidity
function _isContract(address target) private view returns (bool)
```

_Returns whether an address is a contract._

#### Return Values

| Name | Type | Description                   |
| ---- | ---- | ----------------------------- |
| \[0] | bool | Bool target address has code. |

## MixinVoting

### propose

```solidity
function propose(struct IGovernanceVoting.ProposedAction[] actions, string description) external returns (uint256 proposalId)
```

Creates a proposal on the the given actions. Must have at least `proposalThreshold`.

_Must have at least `proposalThreshold` of voting power to call this function._

#### Parameters

| Name        | Type                                       | Description                                                |
| ----------- | ------------------------------------------ | ---------------------------------------------------------- |
| actions     | struct IGovernanceVoting.ProposedAction\[] | The proposed actions. An action specifies a contract call. |
| description | string                                     | A text description for the proposal.                       |

#### Return Values

| Name       | Type    | Description                           |
| ---------- | ------- | ------------------------------------- |
| proposalId | uint256 | The ID of the newly created proposal. |

### castVote

```solidity
function castVote(uint256 proposalId, enum IGovernanceVoting.VoteType voteType) external
```

Casts a vote for the given proposal.

_Only callable during the voting period for that proposal. One address can only vote once._

#### Parameters

| Name       | Type                            | Description                                 |
| ---------- | ------------------------------- | ------------------------------------------- |
| proposalId | uint256                         | The ID of the proposal to vote on.          |
| voteType   | enum IGovernanceVoting.VoteType | Whether to support, not support or abstain. |

### castVoteBySignature

```solidity
function castVoteBySignature(uint256 proposalId, enum IGovernanceVoting.VoteType voteType, uint8 v, bytes32 r, bytes32 s) external
```

Casts a vote for the given proposal, by signature.

_Only callable during the voting period for that proposal. One voter can only vote once._

#### Parameters

| Name       | Type                            | Description                                 |
| ---------- | ------------------------------- | ------------------------------------------- |
| proposalId | uint256                         | The ID of the proposal to vote on.          |
| voteType   | enum IGovernanceVoting.VoteType | Whether to support, not support or abstain. |
| v          | uint8                           | the v field of the signature.               |
| r          | bytes32                         | the r field of the signature.               |
| s          | bytes32                         | the s field of the signature.               |

### execute

```solidity
function execute(uint256 proposalId) external payable
```

Executes a proposal that has passed and is currently executable.

#### Parameters

| Name       | Type    | Description                        |
| ---------- | ------- | ---------------------------------- |
| proposalId | uint256 | The ID of the proposal to execute. |

### \_castVote

```solidity
function _castVote(address voter, uint256 proposalId, enum IGovernanceVoting.VoteType voteType) private
```

Casts a vote for the given proposal.

_Only callable during the voting period for that proposal._

## RigoblockGovernanceFactory

### \_parameters

```solidity
struct IRigoblockGovernanceFactory.Parameters _parameters
```

### createGovernance

```solidity
function createGovernance(address implementation, address governanceStrategy, uint256 proposalThreshold, uint256 quorumThreshold, enum IGovernanceState.TimeType timeType, string name) external returns (address governance)
```

Creates a new governance proxy.

#### Parameters

| Name               | Type                           | Description                                           |
| ------------------ | ------------------------------ | ----------------------------------------------------- |
| implementation     | address                        | Address of the governance implementation contract.    |
| governanceStrategy | address                        | Address of the voting strategy.                       |
| proposalThreshold  | uint256                        | Number of votes required for creating a new proposal. |
| quorumThreshold    | uint256                        | Number of votes required for execution.               |
| timeType           | enum IGovernanceState.TimeType | Enum of time type (block number or timestamp).        |
| name               | string                         | Human readable string of the name.                    |

#### Return Values

| Name       | Type    | Description                    |
| ---------- | ------- | ------------------------------ |
| governance | address | Address of the new governance. |

### parameters

```solidity
function parameters() external view returns (struct IRigoblockGovernanceFactory.Parameters)
```

Returns the governance initialization parameters at proxy deploy.

#### Return Values

| Name | Type                                          | Description                         |
| ---- | --------------------------------------------- | ----------------------------------- |
| \[0] | struct IRigoblockGovernanceFactory.Parameters | Tuple of the governance parameters. |

### \_isContract

```solidity
function _isContract(address target) private view returns (bool)
```

_Returns whether an address is a contract._

#### Return Values

| Name | Type | Description                   |
| ---- | ---- | ----------------------------- |
| \[0] | bool | Bool target address has code. |

## RigoblockGovernanceProxy

### Upgraded

```solidity
event Upgraded(address newImplementation)
```

Emitted when implementation written to proxy storage.

_Emitted also at first variable initialization._

#### Parameters

| Name              | Type    | Description                        |
| ----------------- | ------- | ---------------------------------- |
| newImplementation | address | Address of the new implementation. |

### \_IMPLEMENTATION\_SLOT

```solidity
bytes32 _IMPLEMENTATION_SLOT
```

### constructor

```solidity
constructor() public payable
```

Sets address of implementation contract.

### fallback

```solidity
fallback() external payable
```

Fallback function forwards all transactions and returns all received return data.

### receive

```solidity
receive() external payable
```

Allows this contract to receive ether.

### ImplementationSlot

```solidity
struct ImplementationSlot {
  address implementation;
}
```

### \_getImplementation

```solidity
function _getImplementation() private pure returns (struct RigoblockGovernanceProxy.ImplementationSlot s)
```

Method to read/write from/to implementation slot.

#### Return Values

| Name | Type                                               | Description                                    |
| ---- | -------------------------------------------------- | ---------------------------------------------- |
| s    | struct RigoblockGovernanceProxy.ImplementationSlot | Storage slot of the governance implementation. |

## RigoblockGovernanceStrategy

### \_stakingProxy

```solidity
address _stakingProxy
```

### \_votingPeriod

```solidity
uint256 _votingPeriod
```

### constructor

```solidity
constructor(address stakingProxy) public
```

### assertValidInitParams

```solidity
function assertValidInitParams(struct IRigoblockGovernanceFactory.Parameters params) external view
```

Reverts if initialization paramters are incorrect.

_Only used at initialization, as params deleted from factory storage after setup._

#### Parameters

| Name   | Type                                          | Description                  |
| ------ | --------------------------------------------- | ---------------------------- |
| params | struct IRigoblockGovernanceFactory.Parameters | Tuple of factory parameters. |

### assertValidThresholds

```solidity
function assertValidThresholds(uint256 proposalThreshold, uint256 quorumThreshold) public view
```

Reverts if thresholds are incorrect.

#### Parameters

| Name              | Type    | Description                                         |
| ----------------- | ------- | --------------------------------------------------- |
| proposalThreshold | uint256 | Number of votes required to make a proposal.        |
| quorumThreshold   | uint256 | Number of votes required for a proposal to succeed. |

### getProposalState

```solidity
function getProposalState(struct IGovernanceState.Proposal proposal, uint256 minimumQuorum) external view returns (enum IGovernanceState.ProposalState)
```

Returns the state of a proposal for a required quorum.

#### Parameters

| Name          | Type                             | Description                                      |
| ------------- | -------------------------------- | ------------------------------------------------ |
| proposal      | struct IGovernanceState.Proposal | Tuple of the proposal.                           |
| minimumQuorum | uint256                          | Number of votes required for a proposal to pass. |

#### Return Values

| Name | Type                                | Description                  |
| ---- | ----------------------------------- | ---------------------------- |
| \[0] | enum IGovernanceState.ProposalState | Tuple of the proposal state. |

### \_qualifiedConsensus

```solidity
function _qualifiedConsensus(struct IGovernanceState.Proposal proposal, uint256 minimumQuorum) private view returns (bool)
```

### getVotingPower

```solidity
function getVotingPower(address account) public view returns (uint256)
```

Return a user's voting power.

#### Parameters

| Name    | Type    | Description                 |
| ------- | ------- | --------------------------- |
| account | address | Address to check votes for. |

### votingPeriod

```solidity
function votingPeriod() public view returns (uint256)
```

Return the voting period.

#### Return Values

| Name | Type    | Description                           |
| ---- | ------- | ------------------------------------- |
| \[0] | uint256 | Number of seconds of period duration. |

### votingTimestamps

```solidity
function votingTimestamps() public view returns (uint256 startBlockOrTime, uint256 endBlockOrTime)
```

Returns the voting timestamps.

#### Return Values

| Name             | Type    | Description                     |
| ---------------- | ------- | ------------------------------- |
| startBlockOrTime | uint256 | Timestamp when proposal starts. |
| endBlockOrTime   | uint256 | Timestamp when voting ends.     |

### \_assertValidProposalThreshold

```solidity
function _assertValidProposalThreshold(uint256 proposalThreshold) private view
```

### \_assertValidQuorumThreshold

```solidity
function _assertValidQuorumThreshold(uint256 quorumThreshold) private view
```

### \_getStakingProxy

```solidity
function _getStakingProxy() private view returns (address)
```

It is more gas efficient at deploy to reading immutable from internal method.
