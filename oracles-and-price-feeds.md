---
description: Reliable Price Feeds for Token Prices
---

# Oracles and Price Feeds

## Overview

Oracles are essential for providing reliable price data to smart contracts in decentralized finance (DeFi). Our oracle system, built as a Uniswap V4 hook, delivers **block-manipulation resistant** price feeds for on-chain token pairs, across chains using consensus mechanisms like Proof of Stake (PoS), Proof of Authority (PoA), and sequencer-based systems (e.g., Ethereum L2s). Our oracle offers a robust, on-chain solution optimized for DeFi applications requiring secure and manipulation-resistant price data.

## Key Features

* **Proof of Stake Resistance:** Mitigates price manipulation across various consensus mechanisms by leveraging Uniswap V4 hooks and automatic backrunning.
* **On-Chain Price Feeds:** Provides pricing data for on-chain token pairs, eliminating reliance on off-chain data sources.
* **Automated Backrunning:** Executes backrunning within the hook to revert price manipulations, ensuring minimal user intervention.
* **Single Oracle per Trading Pair:** Simplifies deployment with one oracle per trading pair, reducing complexity and attack vectors.
* **Truncated Geomean Oracles:** Caps tick movement per block to limit manipulation, with safeguards for multi-block scenarios.
* **Full Range Liquidity:** Uses maximum tick spacing and full range to ensure uniform liquidity, enhancing resistance to manipulation.

## **Architecture**

The oracle system is built as a Uniswap V4 hook, capturing price observations at the start of each block and processing them to resist manipulation. Key components include:

* **Observation Storage:** Records the last block’s price observation at the first transaction, capturing a non-manipulated state.
* **Automatic Backrunning:** Protects against price manipulations within the same or subsequent blocks by executing backrunning transactions, limiting tick delta to \~2280 ticks per block.
* **Tick Spacing and Range:** Configures pools with maximum tick spacing and full range for robust liquidity and manipulation resistance.
* **Manipulation Detection:** Monitors tick deltas to detect and counteract manipulation attempts, increasing the cost of attacks.

## Block-Manipulation Resistance

The oracle is designed to resist price manipulation in various consensus environments:

* **PoS Chains:** Mitigates multi-block attacks by limiting tick movement and using backrunning to deter attackers, even when validators can predict block proposers.
* **PoA and Sequencer-Based Systems:** Ensures price feed integrity in Ethereum L2s or other chains with centralized or semi-centralized block production.
* **Economic Deterrence:** Automatic backrunning raises the financial cost of manipulation, making attacks economically unviable.

## **Integration Guide**

**Prerequisites**

* Familiarity with Uniswap V4 and its hook system.
* Access to an Ethereum development environment (e.g., Hardhat, Foundry).
* For testing, use the Sepolia testnet where the oracle hook is deployed at: [0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4](https://sepolia.etherscan.io/address/0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4).

## Using an Existing Price Feed

To retrieve price data from an existing Uniswap V4 pool with liquidity and an attached oracle hook, call the observe method on the hook contract.

#### &#xD; **Example: Fetching Price Data (TWAP)**

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

interface IOracleHook {
    function observe(uint32[] calldata secondsAgos) external view returns (int56[] memory tickCumulatives, uint160[] memory secondsPerLiquidityCumulativeX128s);
}

contract PriceFeedConsumer {
    IOracleHook public oracleHook = IOracleHook(0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4);

    function getLatestPrice() external view returns (int24 tick) {
        uint32[] memory secondsAgos = new uint32[](2);
        secondsAgos[0] = 0; // Latest observation
        secondsAgos[1] = 1; // Previous observation

        (int56[] memory tickCumulatives, ) = oracleHook.observe(secondsAgos);
        tick = int24((tickCumulatives[0] - tickCumulatives[1]) / 1); // Calculate average tick
        return tick;
    }
}
```

* **Query TWAP tick on Sepolia:** Use the hook address 0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4 to interact with the oracle.
* **Tick to Price:** Convert the returned tick to a price using Uniswap’s tick-to-price formula.

#### Creating a New Price Feed

To create a new price feed for a token pair:

* Initialize a Uniswap V4 Pool:
  * Initialize a new pool via the Uniswap V4 Pool Manager, using the oracle hook.
  * Set maximum tick spacing and full range liquidity (initialization will fail otherwise).

```
// Example: Initialize pool with oracle hook (simplified)
import "@uniswap/v4-core/contracts/interfaces/IPoolManager.sol";

contract PoolInitializer {
    IPoolManager public poolManager = IPoolManager(POOL_MANAGER_ADDRESS);
    address public oracleHook = 0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4;

    function createPool(address token0, address token1, uint24 fee, int24 tickSpacing) external {
        poolManager.initialize(token0, token1, fee, tickSpacing, oracleHook);
    }
}
```

**Add Liquidity:**

* Provide liquidity to the pool to enable trading and price discovery.
* Ensure full range liquidity to align with the oracle’s manipulation-resistant design.

**Verify Oracle Functionality:**

* Call the observe method to confirm the oracle is providing price data.
* Test manipulation resistance by simulating large swaps and verifying tick stability.

## **Automatic Backrunning**

The oracle hook automatically executes backrunning to counteract price manipulations, requiring no user intervention. The hook:

* Monitors tick deltas during swaps.
* Triggers backrunning if the tick delta exceeds \~2280 ticks per block.
* Reverts manipulations by adjusting liquidity or executing counter-swaps within the same or next block.

This ensures the price feed remains robust without additional user setup.

## **Further Reading**

* [RigoBlock Oracle Blog Post](https://mirror.xyz/rigoblock.eth/yKAD5uYyH0KwfdsOxzt0MyppkFJZzXkxAFeufPGVA2M)
* [Sepolia Oracle Hook](https://sepolia.etherscan.io/address/0xa2e4Ac052B02EeD76bD997F0a2cD3999A9f03AC4)
