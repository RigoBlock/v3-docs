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
* Choose an available deployment (listed at the end of this page).

## Using an Existing Price Feed

To retrieve price data from an existing Uniswap V4 pool with liquidity and an attached oracle hook, call the observe method on the hook contract.

#### &#xD; **Example: Fetching Price Data (TWAP)**

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import {OracleLibrary} from "@uniswap/v3-periphery/contracts/libraries/OracleLibrary.sol";
import {IHooks} from "@uniswap/v4-core/src/interfaces/IHooks.sol";
import {TickMath} from "@uniswap/v4-core/src/libraries/TickMath.sol";
import {PoolKey} from "@uniswap/v4-core/src/types/PoolKey.sol";

interface IOracle {
    function observe(
        PoolKey calldata key,
        uint32[] calldata secondsAgos
    ) external view returns (int48[] memory tickCumulatives, uint144[] memory secondsPerLiquidityCumulativeX128s);
}

contract PriceFeedConsumer {
    IOracle public backGeoOracle;
    
    constructor(IOracle _backGeoOracle) {
        backGeoOracle = _backGeoOracle;
    }

    function getTwapTick(address tokenA, address tokenB) external view returns (int24 twapTick) {
        uint32[] memory secondsAgos = new uint32[](2);
        secondsAgos[0] = 0; // Latest observation
        uint32 twapWindow = 1; // 1-second TWAP
        secondsAgos[1] = twapWindow; // Previous observation
        
        PoolKey memory key = PoolKey({
            currency0: Currency.wrap(tokenA),
            currency1: Currency.wrap(tokenB),
            fee: 0,
            tickSpacing: TickMath.MAX_TICK_SPACING,
            hooks: IHooks(backGeoOracle)
        });

        (int56[] memory tickCumulatives, ) = oracleHook.observe(key, secondsAgos);
        twapTick = int24((tickCumulatives[0] - tickCumulatives[1]) / int56(uint56(twapWindow))); // Calculate average tick
        return twapTick;
    }
}
```

* **Query TWAP tick:** Use the different of two tick points to extract the TWAP. Make sure you set a time delta appropriate for your application (i.e. 1-minute, 5-minutes).
* **Tick to Price:** Convert the returned tick to a price using Uniswap’s tick-to-price formula.

#### **Example: Converting token amount from base to quote using TWAP**

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import {OracleLibrary} from "@uniswap/v3-periphery/contracts/libraries/OracleLibrary.sol";
import {IHooks} from "@uniswap/v4-core/src/interfaces/IHooks.sol";
import {TickMath} from "@uniswap/v4-core/src/libraries/TickMath.sol";
import {PoolKey} from "@uniswap/v4-core/src/types/PoolKey.sol";

interface IOracle {
    function observe(
        PoolKey calldata key,
        uint32[] calldata secondsAgos
    ) external view returns (int48[] memory tickCumulatives, uint144[] memory secondsPerLiquidityCumulativeX128s);
}

/// @notice derived from Euler's UniswapV3Oracle https://github.com/euler-xyz/euler-price-oracle/blob/master/src/adapter/uniswap/UniswapV3Oracle.sol
contract PriceFeedConsumer {
    error PriceOracle_Overflow();

    IOracle public backGeoOracle;
    
    constructor(IOracle _backGeoOracle) {
        backGeoOracle = _backGeoOracle;
    }

    function getQuote(uint256 inAmount, address base, address quote) external view returns (uint256) {
        // Size limitation enforced by the pool.
        if (inAmount > type(uint128).max) revert PriceOracle_Overflow();

        uint32[] memory secondsAgos = new uint32[](2);
        uint32 twapWindow = 300; // 5-minute TWAP
        secondsAgos[0] = twapWindow;

        PoolKey memory key = PoolKey({
            currency0: Currency.wrap(tokenA),
            currency1: Currency.wrap(tokenB),
            fee: 0,
            tickSpacing: TickMath.MAX_TICK_SPACING,
            hooks: IHooks(backGeoOracle)
        });

        // Calculate the mean tick over the twap window.
        (int48[] memory tickCumulatives,) = IOracle(backGeoOracle).observe(key, secondsAgos);
        int56 tickCumulativesDelta = tickCumulatives[1] - tickCumulatives[0];
        int24 tick = int24(tickCumulativesDelta / int56(uint56(twapWindow)));
        if (tickCumulativesDelta < 0 && (tickCumulativesDelta % int56(uint56(twapWindow)) != 0)) tick--;
        return OracleLibrary.getQuoteAtTick(tick, uint128(inAmount), base, quote);
    }
}
```

## Creating a New Price Feed

To create a new price feed for a token pair:

* Initialize a Uniswap V4 Pool:
  * Initialize a new pool via the Uniswap V4 Pool Manager, using the oracle hook.
  * Set maximum tick spacing and full range liquidity (initialization will fail otherwise).
  * Be mindful about correctly setting the initial price, as otherwise the hook will need to get in par with other pools ≃ 10% per block (manually or via arbitrage) once liquidity is provided (10% per second on sub-second chains).

```
// Example: Initialize pool with oracle hook (simplified)
import "@uniswap/v4-core/contracts/interfaces/IPoolManager.sol";

contract PoolInitializer {
    address public immutable oracleHook;

    IPoolManager public poolManager = IPoolManager(POSM_ADDRESS);
    
    constructor(address backGeoOracle) {
        oracleHook = backGeoOracle;
    }

    /// @notice fee must be 0, tickSpacing must be TickMath.MAX_TICK_SPACING
    function createPool(
        address token0,
        address token1,
        uint24 fee,
        int24 tickSpacing
    ) external {
        poolManager.initialize(token0, token1, fee, tickSpacing, oracleHook);
    }
}
```

**Add Liquidity:**

* Provide liquidity to the pool to enable trading and price discovery (full range).
* Your position will be modified via arbitraged if price feed tick is not in line with market.

**Verify Oracle Functionality:**

* Call the observe method to confirm the oracle is providing price data.
* Test manipulation resistance by simulating large swaps and verifying tick stability.
* If you created the price feed, make sure you increase pair cardinality by calling the \`increaseCardinalityNext\` method in the BackGeoOracle contract, to increase its robustness (with a cardinality of 1, the extracted TWAP will only return the last stored tick, making it susceptible to manipulation).

## **Automatic Backrunning**

The oracle hook automatically executes backrunning to counteract price manipulations, requiring no user intervention. The hook:

* Monitors tick deltas during swaps.
* Triggers backrunning if the tick delta exceeds \~2280 ticks per block.
* Reverts manipulations by adjusting liquidity or executing counter-swaps within the same or next block.

This ensures the price feed remains robust without additional user setup.

The Backrunning Geomean Oracle has been selected as part of the Uniswap Foundation Security Fund (UFSF) Cohort 2. The smart contracts have been audited by [33Audits](https://www.33audits.xyz/). The audit report can be found in the [Github repository](https://github.com/RigoBlock/back-geo-oracle/tree/main/audits).

## Oracle Deployments

#### Mainnet Deployments

1. [Ethereum](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0xB13250f0Dc8ec6dE297E81CDA8142DB51860BaC4](https://etherscan.io/address/0xB13250f0Dc8ec6dE297E81CDA8142DB51860BaC4)
2. [Arbitrum](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x3043e182047F8696dFE483535785ed1C3681baC4](https://arbiscan.io/address/0x3043e182047F8696dFE483535785ed1C3681baC4)
3. [Base](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x59f39091Fd6f47e9D0bCB466F74e305f1709BAC4](https://basescan.org/address/0x59f39091Fd6f47e9D0bCB466F74e305f1709BAC4)
4. [Bsc](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x77B2051204306786934BE8bEC29a48584E133aC4](https://bscscan.com/address/0x77B2051204306786934BE8bEC29a48584E133aC4)
5. [Optimism](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x79234983dED8EAA571873fffe94e437e11C7FaC4](https://optimistic.etherscan.io/address/0x79234983dED8EAA571873fffe94e437e11C7FaC4)
6. [Polygon](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x1D8691A1A7d53B60DeDd99D8079E026cB0E5bac4](https://polygonscan.com/address/0x1D8691A1A7d53B60DeDd99D8079E026cB0E5bac4)
7. [Unichain](https://github.com/RigoBlock/back-geo-oracle/blob/main/src/BackGeoOracle.sol) -> [0x54bd666eA7FD8d5404c0593Eab3Dcf9b6E2A3aC4](https://uniscan.xyz/address/0x54bd666eA7FD8d5404c0593Eab3Dcf9b6E2A3aC4)

#### Testnet Deployments

1. Sepolia [0xE39CAf28BF7C238A42D4CDffB96587862F41bAC4](https://sepolia.etherscan.io/address/0xE39CAf28BF7C238A42D4CDffB96587862F41bAC4)

## **Further Reading**

* [RigoBlock Oracle Blog Post](https://mirror.xyz/rigoblock.eth/yKAD5uYyH0KwfdsOxzt0MyppkFJZzXkxAFeufPGVA2M)
* [UFSF](https://valiant-polo-a06.notion.site/Uniswap-Foundation-Security-Fund-Marketplace-1812019bf073802fa41dc30f88d8f513)
