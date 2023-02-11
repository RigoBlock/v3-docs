# Selectors

## Whitelisted Methods

can be called by Rigoblock pools

### EUpgrade

```
"466f3dc3": "upgradeImplementation()"
"2d6b3a6b": "getBeacon()"
```

### EWhitelist

```
"ab37f486": "isWhitelistedToken(address)"
```

### AMulticall

```
"ac9650d8": "multicall(bytes[])"
"5ae401dc": "multicall(uint256,bytes[])"
"1f0464d1": "multicall(bytes32,bytes[])"
```

### ASelfCustody

```
@notice mainnet, goerli only
"318698a7": "transferToSelfCustody(address,address,uint256)"
"6d6b09e9": "poolGrgShortfall(address)"
"4f8554da": "grgVault()"
```

### AStaking

```
"a694fc3a": "stake(uint256)"
"4aace835": "undelegateStake(uint256)",
"2e17de78": "unstake(uint256)",
"b880660b": "withdrawDelegatorRewards()"
```

### AUniswap

```
"88316456": "mint((address,address,uint24,int24,int24,uint256,uint256,uint256,uint256,address,uint256))",
"c391b77c": "uniswapv3Npm()",
"3fc8cef3": "weth()"
"42966c68": "burn(uint256)",
"fc6f7865": "collect((uint256,address,uint128,uint128))",
"13ead562": "createAndInitializePoolIfNecessary(address,address,uint24,uint160)",
"0c49ccbe": "decreaseLiquidity((uint256,uint128,uint256,uint256,uint256))",
"219f5d17": "increaseLiquidity((uint256,uint256,uint256,uint256,uint256,uint256))",
"12210e8a": "refundETH()",
"df2ab5bb": "sweepToken(address,uint256,address)",
"49404b7c": "unwrapWETH9(uint256,address)",
"1c58db4f": "wrapETH(uint256)",
"472b43f3": "swapExactTokensForTokens(uint256,uint256,address[],address)",
"42712a67": "swapTokensForExactTokens(uint256,uint256,address[],address)",
"04e45aaf": "exactInputSingle(ExactInputSingleParams)",
"b858183f": "exactInput(ExactInputParams)",
"5023b4df": "exactOutputSingle(ExactOutputSingleParams)",
"09b81346": "exactOutput(ExactOutputParams)",
"e90a182f": "sweepToken(address,uint256,address)",
"e0e189a0": "sweepTokenWithFee(address,uint256,address,uint256,address)",
"3068c554": "sweepTokenWithFee(address,uint256,uint256,address)",
(TODO: check DUPLICATE)
"49404b7c": "unwrapWETH9(uint256,address)",
"49616997": "unwrapWETH9(uint256)",
"9b2c0a37": "unwrapWETH9WithFee(uint256,address,uint256,address)",
"d4ef38de": "unwrapWETH9WithFee(uint256,uint256,address)"
```

### AGovernance

```
"56781388": "castVote(uint256, VoteType)",
"fe0d94c1": "execute(uint256)",
"367015bb": "propose(Proposal, string)"
```
