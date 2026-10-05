# MixinStorage

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract MixinStorage is MixinImmutables
```


## Structs info

### ParamsWrapper

```solidity
struct ParamsWrapper {
	IGovernanceState.GovernanceParameters governanceParameters;
}
```


### AddressSlot

```solidity
struct AddressSlot {
	address value;
}
```


### StringSlot

```solidity
struct StringSlot {
	string value;
}
```


### UintSlot

```solidity
struct UintSlot {
	uint256 value;
}
```


### ProposalByIndex

```solidity
struct ProposalByIndex {
	mapping(uint256 => IGovernanceState.Proposal) proposalById;
}
```


### ProposalQuorumByIndex

```solidity
struct ProposalQuorumByIndex {
	mapping(uint256 => uint256) proposalQuorumById;
}
```


### ActionByIndex

```solidity
struct ActionByIndex {
	mapping(uint256 => mapping(uint256 => IGovernanceVoting.ProposedAction)) proposedActionbyIndex;
}
```


### UserReceipt

```solidity
struct UserReceipt {
	mapping(uint256 => mapping(address => IGovernanceState.Receipt)) userReceiptByProposal;
}
```


### VoterNonces

```solidity
struct VoterNonces {
	mapping(address => uint256) nonceByVoter;
}
```


### ExpectedSequenceSlot

```solidity
struct ExpectedSequenceSlot {
	uint64 value;
}
```


### ProposalMeta

```solidity
struct ProposalMeta {
	address proposer;
	bool canceled;
}
```


### ProposalMetaByIndex

```solidity
struct ProposalMetaByIndex {
	mapping(uint256 => MixinStorage.ProposalMeta) proposalMetaById;
}
```


### OzProposalIdByHash

```solidity
struct OzProposalIdByHash {
	mapping(bytes32 => uint256) idByHash;
}
```

