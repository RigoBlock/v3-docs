# IGovernanceStrategy

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceStrategy
```


## Functions info

### assertValidInitParams (0x2e100214)

```solidity
function assertValidInitParams(
    IRigoblockGovernanceFactory.Parameters calldata params
) external view
```

Reverts if initialization paramters are incorrect.

Only used at initialization, as params deleted from factory storage after setup.


Parameters:

| Name   | Type                                          | Description                  |
| :----- | :-------------------------------------------- | :--------------------------- |
| params | struct IRigoblockGovernanceFactory.Parameters | Tuple of factory parameters. |

### assertValidProposalThreshold (0xa564b600)

```solidity
function assertValidProposalThreshold(uint256 proposalThreshold) external view
```

Reverts if the proposal threshold is incorrect.


Parameters:

| Name              | Type    | Description                                  |
| :---------------- | :------ | :------------------------------------------- |
| proposalThreshold | uint256 | Number of votes required to make a proposal. |

### assertValidQuorumThreshold (0x41fc31a7)

```solidity
function assertValidQuorumThreshold(uint256 quorumThreshold) external view
```

Reverts if the quorum threshold is incorrect.


Parameters:

| Name            | Type    | Description                                         |
| :-------------- | :------ | :-------------------------------------------------- |
| quorumThreshold | uint256 | Number of votes required for a proposal to succeed. |

### getProposalState (0xad1d8f45)

```solidity
function getProposalState(
    IGovernanceState.Proposal calldata proposal,
    uint256 minimumQuorum,
    TimeType timeType
) external view returns (ProposalStatus)
```

Returns the state of a proposal for a required quorum.

Must use the same time reference as `timeType` and revert for unsupported time types.
See docs/governance/STRATEGY.md.


Parameters:

| Name          | Type                             | Description                                           |
| :------------ | :------------------------------- | :---------------------------------------------------- |
| proposal      | struct IGovernanceState.Proposal | Tuple of the proposal.                                |
| minimumQuorum | uint256                          | Number of votes required for a proposal to pass.      |
| timeType      | enum TimeType                    | Time reference used by the proposal's voting period.  |


Return values:

| Name | Type                | Description                  |
| :--- | :------------------ | :--------------------------- |
| [0]  | enum ProposalStatus | Tuple of the proposal state. |

### votingPeriod (0x02a251a3)

```solidity
function votingPeriod() external view returns (uint256)
```

Return the voting period.

Informational only: the enforceable window is the one returned by votingTimestamps.


Return values:

| Name | Type    | Description                                                                          |
| :--- | :------ | :----------------------------------------------------------------------------------- |
| [0]  | uint256 | Number of blocks or seconds of period duration, matching the governance's time type. |

### votingTimestamps (0x25bbc354)

```solidity
function votingTimestamps(
    TimeType timeType
) external view returns (uint256 startBlockOrTime, uint256 endBlockOrTime)
```

Returns the voting timestamps.

Must produce start/end values expressed in the same unit as `timeType` (block numbers
for TimeType.Blocknumber, timestamps for TimeType.Timestamp). See getProposalState.


Parameters:

| Name     | Type          | Description                                           |
| :------- | :------------ | :---------------------------------------------------- |
| timeType | enum TimeType | Time reference used by the proposal's voting period.  |


Return values:

| Name             | Type    | Description                      |
| :--------------- | :------ | :------------------------------- |
| startBlockOrTime | uint256 | Timestamp when proposal starts.  |
| endBlockOrTime   | uint256 | Timestamp when voting ends.      |

### getVotingPower (0xbb4d4436)

```solidity
function getVotingPower(address account) external view returns (uint256)
```

Return a user's voting power.


Parameters:

| Name    | Type    | Description                 |
| :------ | :------ | :-------------------------- |
| account | address | Address to check votes for. |

### beforePropose (0xcab9110e)

```solidity
function beforePropose(
    IGovernanceVoting.ProposedAction calldata action
) external view returns (IGovernanceVoting.ProposedAction memory)
```

Validates and optionally modifies an action before it is stored as part of a proposal.


Parameters:

| Name   | Type                                    | Description              |
| :----- | :-------------------------------------- | :----------------------- |
| action | struct IGovernanceVoting.ProposedAction | The action to validate.  |


Return values:

| Name | Type                                    | Description                               |
| :--- | :-------------------------------------- | :---------------------------------------- |
| [0]  | struct IGovernanceVoting.ProposedAction | The validated (possibly modified) action. |

### beforeExecute (0xfa05b6f6)

```solidity
function beforeExecute(
    IGovernanceVoting.ProposedAction calldata action
) external view returns (IGovernanceVoting.ProposedAction memory)
```

Returns the action as it should be executed, optionally modifying the value.


Parameters:

| Name   | Type                                    | Description             |
| :----- | :-------------------------------------- | :---------------------- |
| action | struct IGovernanceVoting.ProposedAction | The action to execute.  |


Return values:

| Name | Type                                    | Description            |
| :--- | :-------------------------------------- | :--------------------- |
| [0]  | struct IGovernanceVoting.ProposedAction | The action to execute. |

### wormhole (0x84acd1bb)

```solidity
function wormhole() external view returns (address)
```

Returns the Wormhole core contract used for cross-chain governance.


Return values:

| Name | Type    | Description                                                                                                                      |
| :--- | :------ | :------------------------------------------------------------------------------------------------------------------------------- |
| [0]  | address | Address of the Wormhole core contract, or the zero address if this chain is not configured as a cross-chain governance receiver. |

### wormholeChainId (0x793e64e3)

```solidity
function wormholeChainId() external view returns (uint16)
```

Returns the Wormhole chain id of the chain this strategy is deployed on.