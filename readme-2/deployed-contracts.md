# deployed contracts

## default contracts addresses on networks:

```
1: mainnet, 
5: goerli,
10: optimism,
137: polygon,
42161: arbitrum 
```

### deps

```
Authority 0xe35129A1E0BdB913CF6Fd8332E9d3533b5F41472
PoolRegistry 0x06767e8090bA5c4Eca89ED00C3A719909D503ED6
```

### core

```
RigoblockV3Pool 0xeb0c08Ad44af89BcBB5Ed6dD28caD452311B8516
RigoblockPoolProxyFactory 0x8DE8895ddD702d9a216E640966A98e08c9228f24
```

### extensions

```
EUpgrade 0x64BcA3673c8990B11225E9f49E6da554180690fc
EWhitelist 0xB43baD2638696F8bC82247B92bD56B8DF37d89aB
AMulticall 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC
AUniswap 0xC1ad7e8ea82f2f5129428a46Eb968D08CD40cb92
```

### mainnet-only, goerli-only

#### mainnet

```
ERC20Proxy 0x8C96182c1B2FE5c49b1bc9d9e039e369f131ED37
RigoToken 0x4FbB350052Bca5417566f188eB2EBCE5b19BC964
Inflation 0x3c602D3C6140073DF26BC1f42196484311C946AB
ProofOfPerformance 0xC3736344ee0bcE9bDe5D231060f03990b798f030
GrgVault 0xfbd2588b170Ff776eBb1aBbB58C0fbE3ffFe1931
Staking 0x10bffaF04448313Dd64476072391e7f9F7f670ca
StakingProxy 0x730dDf7b602dB822043e0409d8926440395e07fE
AStaking 0x70A82fd79983Eb659874A16f56Df593ccE050e77
ASelfCustody 0x32Caa23B354427ea9A27Ed6A122C04b3c96d071E
```

#### goerli

```
ERC20Proxy 0x28891F41eA506Ba7eA3Be9f2075AB0aa8b81dD29
RigoToken 0x076C619e7ebaBe40746106B66bFBed731F2c1339
Inflation 0x1950676fe511d665C35B2E3748B837045FcD638b
ProofOfPerformance 0x9CE56818c01bCF9bbCa533d2db4b19e85e53a000
GrgVault 0x58b5FBe3e8F86a3f22BB9e47129a9FDE4702c221
Staking 0x25ACe36b92C163194a812819CE960aF2d25AC81A
StakingProxy 0x6C4594aa0CBcb8315E88EFdb11675c09A7a5f444
AStaking 0x360343aBCbe5e34dE1e2e33f332601d17F9E4221
ASelfCustody 0x919e73912510Ee303A52C6A7ddAEbB4ffE2376a1
```

### bsc (diff. deterministic deployment factory results in diff. addresses)

```
56: bsc
```

#### deps

```
Authority 0x3B3b08ACf713C06073D86107345E90AF9eE36569
PoolRegistry 0xA36204A59f93388B8076aB3ba40C5f15650e7359
```

#### core

```
RigoblockV3Pool 0x297C433ba14bd50F4F2e56BAC979E0791008c648
RigoblockPoolProxyFactory 0x62fcda78196Ab8a57ecdef3b99465E711a68d293
```

#### extensions

```
EUpgrade 0xdCabDDf637d9a0d67634F4b2D22419d954b0c87a
EWhitelist 0x2221f6D9Fe993B3B308bFC90aC7cddC50Fcdf7A8
AMulticall 0x3bBdbE026F53500dA7d64fe8cf856cf28755D6Cb
AUniswap NA (uniswap does not support bsc)
```

## Whitelisted Methods (can be called by RigoBlock pools)

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

### ASelfCustody (mainnet, goerli only)

```
"318698a7": "transferToSelfCustody(address,address,uint256)"
"6d6b09e9": "poolGrgShortfall(address)"
"4f8554da": "grgVault()"
```

### AStaking (mainnet, goerli only)

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
