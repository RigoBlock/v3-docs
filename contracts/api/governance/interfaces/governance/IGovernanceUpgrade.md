# IGovernanceUpgrade

## Overview

#### License: Apache-2.0-or-later

```solidity
interface IGovernanceUpgrade
```


## Functions info

### updateThresholds (0xc14b8e9c)

```solidity
function updateThresholds(
    uint256 newProposalThreshold,
    uint256 newQuorumThreshold
) external
```

Updates the proposal and quorum thresholds to the given values.

Only callable by the governance contract itself.

Thresholds can only be updated via a successful governance proposal.


Parameters:

| Name                 | Type    | Description                                |
| :------------------- | :------ | :----------------------------------------- |
| newProposalThreshold | uint256 | The new value for the proposal threshold.  |
| newQuorumThreshold   | uint256 | The new value for the quorum threshold.    |

### upgradeImplementation (0x83f94db7)

```solidity
function upgradeImplementation(address newImplementation) external
```

Updates the governance implementation address.

Only callable after successful voting.


Parameters:

| Name              | Type    | Description                                            |
| :---------------- | :------ | :----------------------------------------------------- |
| newImplementation | address | Address of the new governance implementation contract. |

### upgradeStrategy (0x3f4360a5)

```solidity
function upgradeStrategy(address newStrategy) external
```

Updates the governance strategy plugin.

Only callable by the governance contract itself.


Parameters:

| Name        | Type    | Description                           |
| :---------- | :------ | :------------------------------------ |
| newStrategy | address | Address of the new strategy contract. |
