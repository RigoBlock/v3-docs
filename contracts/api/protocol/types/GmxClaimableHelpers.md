# GmxClaimableHelpers

## Overview

#### License: Apache-2.0-or-later

```solidity
library GmxClaimableHelpers
```


## Functions info

### getClaimableFundingAmount

```solidity
function getClaimableFundingAmount(
    address market,
    address token,
    address account
) internal view returns (uint256)
```


### getClaimableCollateralAmount

```solidity
function getClaimableCollateralAmount(
    bytes32 amountKey,
    GmxCallbackLib.ClaimableCollateralInfo memory info,
    address account
) internal view returns (uint256 claimableAmount_)
```

