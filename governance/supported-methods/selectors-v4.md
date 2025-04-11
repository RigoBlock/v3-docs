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

<pre><code><strong>"49616997": "unwrapWETH9(uint256)",
</strong>"49404b7c": "unwrapWETH9(uint256,address)",
"1c58db4f": "wrapETH(uint256)",
</code></pre>

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
