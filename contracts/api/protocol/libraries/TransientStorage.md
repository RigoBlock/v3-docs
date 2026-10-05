# TransientStorage

## Overview

#### License: Apache-2.0-or-later

```solidity
library TransientStorage
```


## Functions info

### store

```solidity
function store(Int256 slot, address token, int256 value) internal
```

Stores a mapping of token addresses to int256 values
### get

```solidity
function get(Int256 slot, address token) internal view returns (int256)
```


### storeBalance

```solidity
function storeBalance(address token, int256 balance) internal
```


### getBalance

```solidity
function getBalance(address token) internal view returns (int256)
```


### storeTwap

```solidity
function storeTwap(address token, int24 twap) internal
```


### getTwap

```solidity
function getTwap(address token) internal view returns (int24)
```


### setDonationLock

```solidity
function setDonationLock(address token, uint256 balance) internal
```


### getDonationLock

```solidity
function getDonationLock() internal view returns (bool)
```


### setNavLockExempt

```solidity
function setNavLockExempt(bool exempt) internal
```


### getNavLockExempt

```solidity
function getNavLockExempt() internal view returns (bool)
```


### getTemporaryBalance

```solidity
function getTemporaryBalance(
    address token
) internal view returns (uint256, bool)
```


### storeNav

```solidity
function storeNav(uint256 nav) internal
```


### storeAssets

```solidity
function storeAssets(uint256 assets) internal
```


### getStoredNav

```solidity
function getStoredNav() internal view returns (uint256)
```


### getStoredAssets

```solidity
function getStoredAssets() internal view returns (uint256)
```

