# Selectors - V4

## Whitelisted Adapter Methods

can be called by Rigoblock pools to interact with new external applications without requiring an upgrade of the implementation.

### AMulticall

```
"ac9650d8": "multicall(bytes[])"
"5ae401dc": "multicall(uint256,bytes[])"
"1f0464d1": "multicall(bytes32,bytes[])"
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
"42966c68": "burn(uint256)",
"fc6f7865": "collect((uint256,address,uint128,uint128))",
"13ead562": "createAndInitializePoolIfNecessary(address,address,uint24,uint160)",
"0c49ccbe": "decreaseLiquidity((uint256,uint128,uint256,uint256,uint256))",
"b858183f": "exactInput(ExactInputParams)",
"04e45aaf": "exactInputSingle(ExactInputSingleParams)",
"09b81346": "exactOutput(ExactOutputParams)",
"5023b4df": "exactOutputSingle(ExactOutputSingleParams)",
"219f5d17": "increaseLiquidity((uint256,uint256,uint256,uint256,uint256,uint256))",
"88316456": "mint((address,address,uint24,int24,int24,uint256,uint256,uint256,uint256,address,uint256))",
"12210e8a": "refundETH()",
"472b43f3": "swapExactTokensForTokens(uint256,uint256,address[],address)",
"42712a67": "swapTokensForExactTokens(uint256,uint256,address[],address)",
"df2ab5bb": "sweepToken(address,uint256,address)",
"e90a182f": "sweepToken(address,uint256,address)",
"e0e189a0": "sweepTokenWithFee(address,uint256,address,uint256,address)",
"3068c554": "sweepTokenWithFee(address,uint256,uint256,address)",
"49616997": "unwrapWETH9(uint256)",
"49404b7c": "unwrapWETH9(uint256,address)",
"9b2c0a37": "unwrapWETH9WithFee(uint256,address,uint256,address)",
"d4ef38de": "unwrapWETH9WithFee(uint256,uint256,address)"
"1c58db4f": "wrapETH(uint256)",
```

### AUniswapRouter

```
"3593564c": "execute(bytes calldata, bytes[] calldata, uint256)",
"24856bc3": "execute(bytes calldata, bytes[] calldata)"
"dd46508f": "modifyLiquidities(bytes calldata, uint256)"
```

### AGovernance

```
"56781388": "castVote(uint256, VoteType)",
"fe0d94c1": "execute(uint256)",
"367015bb": "propose(Proposal, string)"
```
