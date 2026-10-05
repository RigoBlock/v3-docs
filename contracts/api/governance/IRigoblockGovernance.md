# IRigoblockGovernance

## Overview

#### License: Apache-2.0-or-later

```solidity
abstract contract IRigoblockGovernance is IGovernanceCrosschain, IGovernanceEvents, IGovernanceInitializer, IGovernanceUpgrade, IGovernanceVoting, IGovernanceState, IOZGovernor
```

Inherits the OpenZeppelin Governor and ERC-6372 interfaces so external tooling
compatibility (Tally) is enforced at compile time. Specification: docs/governance/TALLY_COMPAT.md.