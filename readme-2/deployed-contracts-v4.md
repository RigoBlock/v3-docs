# deployed contracts - V4

## Supported Networks

```
Mainnets
1: mainnet (pending governance voting),
10: optimism (pending governance voting),
56: bsc (pending governance voting),
130: unichain,
8453: base (pending governance voting),
42161: arbitrum (pending governance voting)

Testnets
11155111: sepolia
```

## Protocol Addresses

### Deps

```
Authority 0xe35129A1E0BdB913CF6Fd8332E9d3533b5F41472
PoolRegistry 0x06767e8090bA5c4Eca89ED00C3A719909D503ED6
ExtensionsMapDeployer 0x5A69bBe7f8F9dbDBFEa35CeFf33e093C6690d437
```

### Core

```
SmartPool 0xe99DEC5Ba5747E8ADF81Bd58026527c7CB042108
RigoblockPoolProxyFactory 0x8DE8895ddD702d9a216E640966A98e08c9228f24
```

Notice: deterministic deployment requires 0xeb0c08Ad44af89BcBB5Ed6dD28caD452311B8516 as the implementation address in the constructor to obtain the same factory address on new chains.

### Extensions - v4.0.1

```
ExtensionsMap 0x64138543eA39aE7f82E9B16aFfFB0216cFC29B92
EUpgrade 0x6A17ca05b112485Bd5c73215F275Baff7F980ac6
EApps: [
    mainnet: 0x34F63aBB8cA0709F0e5C5A168238BA7f933931EA,
    arbitrum: 0x5545aCb1C55c273001E1136adf25C274cbf8279D,
    base: 0xCf019fBFF29C5146752eBe78bE69969d5d17b8D4,
    bsc: 0x2F4F56B504A432d733eb2a475d3F740246B8d13a,
    optimism: 0xAed60dc2cBcb80989D791A7E2a06d0DD7f82923C,
    unichain: 0xAEdC22891103F031779ed863B454E7A404e24F1C,
    sepolia: 0xaE1af5419d4643Bf91e0e3F9715a6D0B468Ad42c
]
EOracle: [
    mainnet: 0xd223Ed82D7341aB535673340aDf2A1A39F9b9B91,
    arbitrum: 0x4E1A9064b8DA32CA1161CDB10CEE1614bd1506D3,
    base: 0x041Ad9199A4930877BEF1242864D442FA8650266,
    bsc: 0xa917e5Ec3D0421eAA9A68236CC75a0833fbb71C0,
    optimism: 0x18C5eB478bC56532E31598576254564F0ea82b35,
    unichain: 0x180fFD810EFf8b9D976aA925535844A7Faea2A2F,
    sepolia: 0x4AF3dff41D760954534E6E015a12b4cAc15f1FB1
]
```

## Adapters

<pre><code>AMulticall: [
    mainnet: 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC,
    arbitrum: 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC,
    base: 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC,
    bsc: 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC,
    optimism: 0x9cD3CB7CF9392182890d0b5Fe7d92BFD7539afFC,
    unichain: 0x1DC90d2C0d5312dcBC31be6Ccd23b03bf251fFc6,
    sepolia: 0x1DC90d2C0d5312dcBC31be6Ccd23b03bf251fFc6
]
<strong>AStaking: [
</strong>    mainnet: 0x70A82fd79983Eb659874A16f56Df593ccE050e77,
    arbitrum: 0x4672fE808ce3dA430128ad611E251b896abe689E,
    base: 0x9E9abF328B5d1f4b4c66715cB54cA0F66225FBfa,
    bsc: 0xcfDAC3f80a99ebB4d0F951a9C2aa40138992eCD1,
    optimism: 0x21B423Ad9488CAD08E06c50a5DB0F65AAa813254,
    unichain: 0x77f4cF40adC6026B0e8C0df088E0B1459005922c,
    sepolia: 0x7CD4d2c1e816123da38cc6e56b7f893Ff8C3a756
]
AUniswap: [
    mainnet: 0x9cD88265e4960ccFB4c5b5144ddE8A9a04547bAf,
    arbitrum: 0x12d53D40Bf680B1a2f16f6bb77fC58C25D9Ef5f1,
    base: 0x370F2ce1c38Ccc72A42C90CAa1E6899f6A47712A,
    bsc: 0xddBE3Bf04Af3B0D4E4A8b2c7794c08B3bD5A676C,
    optimism: 0x370F2ce1c38Ccc72A42C90CAa1E6899f6A47712A,
    unichain: 0x370F2ce1c38Ccc72A42C90CAa1E6899f6A47712A,
    sepolia: 0xf8A80E8247ed163eB10389B4D01725E140b8D964
]
AUniswapRouter: [
    mainnet: 0x8284C803D82c86618AD3aE108322f6FF76812A74,
    arbitrum: 0xF11C2D97a4AC3a579C5a261EbB11640a3b418077,
    base: 0x8bd932bdE919FE68eC6FCd35eE267d845D54eD00,
    bsc: 0x2f85942545a7DaD5684c49f8dA458C90787121C7,
    optimism: 0x778BbC0326CE44ea139FD1d72c83670b59c2a507,
    unichain: 0x3931fF9e18C8C7CA63069a7Ef56Fef872D774c44,
    sepolia: 0xA22623173929429F5b9a0ddde95566b904232D95
]
</code></pre>

