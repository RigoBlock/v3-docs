# ReentrancyGuardTransient

## Overview

#### License: MIT

```solidity
abstract contract ReentrancyGuardTransient
```

Variant of {ReentrancyGuard} that uses transient storage.

NOTE: This variant only works on networks where EIP-1153 is available.

_Available since v5.1._
## Errors info

### ReentrancyGuardReentrantCall

```solidity
error ReentrancyGuardReentrantCall()
```

Unauthorized reentrant call.
## Modifiers info

### nonReentrant

```solidity
modifier nonReentrant()
```

Prevents a contract from calling itself, directly or indirectly.
Calling a `nonReentrant` function from another `nonReentrant`
function is not supported. It is possible to prevent this from happening
by making the `nonReentrant` function external, and making it call a
`private` function that does the actual work.