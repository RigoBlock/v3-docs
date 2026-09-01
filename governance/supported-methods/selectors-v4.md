# Selectors - V4

## Whitelisted Adapter Methods

can be called by Rigoblock pools to interact with new external applications without requiring an upgrade of the implementation.

### AMulticall

```
"0xac9650d8": "multicall(bytes[])"
"0x5ae401dc": "multicall(uint256,bytes[])"
"0x1f0464d1": "multicall(bytes32,bytes[])"
```

### AStaking

```
"0xa694fc3a": "stake(uint256)"
"0x4aace835": "undelegateStake(uint256)",
"0x2e17de78": "unstake(uint256)",
"0xb880660b": "withdrawDelegatorRewards()"
```

### AUniswap

<pre><code><strong>"0x49616997": "unwrapWETH9(uint256)",
</strong>"0x49404b7c": "unwrapWETH9(uint256,address)",
"0x1c58db4f": "wrapETH(uint256)",
</code></pre>

### AUniswapRouter

```
"0x3593564c": "execute(bytes calldata, bytes[] calldata, uint256)",
"0x24856bc3": "execute(bytes calldata, bytes[] calldata)"
"0xdd46508f": "modifyLiquidities(bytes calldata, uint256)"
```

### AGovernance

```
"0x56781388": "castVote(uint256, VoteType)",
"0xfe0d94c1": "execute(uint256)",
"0x367015bb": "propose(Proposal, string)"
```

### AIntents

```
"0x770d096f": "depositV3(AcrossParams)"
```

### A0xRouter

```
"0x2213bc0b": "exec(address, address, uint256, bytes)"
```

### AGmxV2 (Arbitrum)

<pre><code>"0x7489ec23": "cancelOrder(bytes32)"
"0xe9249b57": "claimCollateral(address[],address[],address[],address)"
"0xc41b1ab3": "claimFundingFees(address[],address[],address)"
<strong>"0xe478512e": "createDecreaseOrder(CreateOrderParams)"
</strong>"0x13b4312f": "createIncreaseOrder(CreateOrderParams)"
"0xdd5baad2": "updateOrder(bytes32,uint256,uint256,uint256,uint256,uint256,bool)"
</code></pre>

### AHyperliquid (HyperEvm)

```
"0x2b2dfd2c": "deposit(uint256,uint32)"
"0xc23c545a": "depositFor(address,uint256,uint32)"
"0x17938e13": "sendRawAction(bytes)"
```
