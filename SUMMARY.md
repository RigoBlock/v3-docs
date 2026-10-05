# Table of contents

* [Welcome](README.md)
* [Introduction to Rigoblock](introduction-to-rigoblock.md)
* [Deployments](deployments/README.md)
  * [Deployed Contracts - v4](deployments/deployed-contracts-v4.md)
  * [Deployed Contracts - v3](deployments/deployed-contracts-v3.md)
  * [Deployed Contracts - Staking](deployments/deployed-contracts-staking.md)
  * [Deployed Contracts - Gov](deployments/deployed-contracts-gov.md)
  * [Deployed Contracts - GRG](deployments/deployed-contracts-grg.md)
  * [v1.5.0](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.5.0)
  * [v1.4.2](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.4.2)
  * [v1.4.1](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.4.1)
  * [v1.3.0](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.3.0)
  * [v1.1.1](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.1.1)
  * [v1.1.0](https://github.com/RigoBlock/V3-deployments/tree/main/src/1.1.0)
* [Oracles and Price Feeds](oracles-and-price-feeds.md)
* [AI Agents](ai-agents/README.md)
  * [TWAP Order](ai-agents/twap-order.md)
  * [Swap Shield](ai-agents/swap-shield.md)
* [Protocol fee](protocol-fee/README.md)
  * [Overview](protocol-fee/overview.md)
  * [Deployments](protocol-fee/deployments.md)
* [Governance](governance/README.md)
  * [Rigoblock Governance](governance/rigoblock-governance.md)
  * [Supported Applications](governance/supported-applications.md)
  * [Supported Methods](governance/supported-methods/README.md)
    * [Selectors - V4](governance/supported-methods/selectors-v4.md)
    * [Selectors - V3](governance/supported-methods/selectors-v3.md)
* [Bug Bounty](bug-bounty/README.md)
  * [Known Issues](bug-bounty/known-issues.md)
* [Contracts](contracts/README.md)
  * [Protocol](contracts/protocol/README.md)
    * [RigoblockPoolExtended](contracts/protocol/rigoblockpoolextended.md)
    * [Core](contracts/protocol/core/README.md)
      * [constants](contracts/protocol/core/constants.md)
      * [immutables](contracts/protocol/core/immutables.md)
      * [storage](contracts/protocol/core/storage.md)
      * [actions](contracts/protocol/core/actions.md)
      * [owner actions](contracts/protocol/core/owner-actions.md)
      * [abstract](contracts/protocol/core/abstract.md)
      * [fallback](contracts/protocol/core/fallback.md)
      * [initializer](contracts/protocol/core/initializer.md)
      * [state](contracts/protocol/core/state.md)
      * [storage accessible](contracts/protocol/core/storage-accessible.md)
    * [Deps](contracts/protocol/deps/README.md)
      * [Authority](contracts/protocol/deps/authority/README.md)
        * [authority docs](contracts/protocol/deps/authority/authority-docs.md)
      * [PoolRegistry](contracts/protocol/deps/poolregistry/README.md)
        * [pool registry docs](contracts/protocol/deps/poolregistry/pool-registry-docs.md)
    * [Extensions](contracts/protocol/extensions/README.md)
      * [AGovernance](contracts/protocol/extensions/agovernance/README.md)
        * [Solidity API](contracts/protocol/extensions/agovernance/solidity-api.md)
      * [AMulticall](contracts/protocol/extensions/amulticall/README.md)
        * [aMulticall docs](contracts/protocol/extensions/amulticall/amulticall-docs.md)
      * [AStaking](contracts/protocol/extensions/astaking/README.md)
        * [aStaking docs](contracts/protocol/extensions/astaking/astaking-docs.md)
      * [AUniswap](contracts/protocol/extensions/auniswap/README.md)
        * [aUniswap docs](contracts/protocol/extensions/auniswap/auniswap-docs.md)
      * [EUpgrade](contracts/protocol/extensions/eupgrade/README.md)
        * [eUpgrade docs](contracts/protocol/extensions/eupgrade/eupgrade-docs.md)
      * [EWhitelist](contracts/protocol/extensions/ewhitelist/README.md)
        * [eWhitelist docs](contracts/protocol/extensions/ewhitelist/ewhitelist-docs.md)
    * [Proxies](contracts/protocol/proxies/README.md)
      * [proxy](contracts/protocol/proxies/proxy/README.md)
        * [proxy docs](contracts/protocol/proxies/proxy/proxy-docs.md)
      * [proxy factory](contracts/protocol/proxies/proxy-factory/README.md)
        * [proxyFactory docs](contracts/protocol/proxies/proxy-factory/proxyfactory-docs.md)
  * [GRG Token](contracts/grg-token/README.md)
    * [RigoToken](contracts/grg-token/rigotoken/README.md)
      * [rigoToken docs](contracts/grg-token/rigotoken/rigotoken-docs.md)
    * [Inflation](contracts/grg-token/inflation/README.md)
      * [inflation docs](contracts/grg-token/inflation/inflation-docs.md)
    * [ProofOfPerformance](contracts/grg-token/proofofperformance/README.md)
      * [pop docs](contracts/grg-token/proofofperformance/pop-docs.md)
  * [GRG Staking](contracts/grg-staking/README.md)
    * [GrgVault](contracts/grg-staking/grgvault/README.md)
      * [grgVault docs](contracts/grg-staking/grgvault/grgvault-docs.md)
    * [StakingProxy](contracts/grg-staking/stakingproxy/README.md)
      * [stakingProxy docs](contracts/grg-staking/stakingproxy/stakingproxy-docs.md)
    * [Staking](contracts/grg-staking/staking/README.md)
      * [staking docs](contracts/grg-staking/staking/staking-docs.md)
  * [Governance](contracts/governance/README.md)
    * [Solidity API](contracts/governance/solidity-api.md)
* ```yaml
  props:
    models: true
    downloadLink: true
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: rigo-x402-api
  ```
<!-- AUTO-GENERATED-API-START -->
* [Solidity API Reference](contracts/api/README.md)
  * Governance
    * [IRigoblockGovernance](contracts/api/governance/IRigoblockGovernance.md)
    * [RigoblockGovernance](contracts/api/governance/RigoblockGovernance.md)
    * Interfaces
      * [IGovernanceStrategy](contracts/api/governance/interfaces/IGovernanceStrategy.md)
      * [IRigoblockGovernanceFactory](contracts/api/governance/interfaces/IRigoblockGovernanceFactory.md)
      * Governance
        * [IGovernanceCrosschain](contracts/api/governance/interfaces/governance/IGovernanceCrosschain.md)
        * [IGovernanceEvents](contracts/api/governance/interfaces/governance/IGovernanceEvents.md)
        * [IGovernanceInitializer](contracts/api/governance/interfaces/governance/IGovernanceInitializer.md)
        * [IGovernanceState](contracts/api/governance/interfaces/governance/IGovernanceState.md)
        * [IGovernanceUpgrade](contracts/api/governance/interfaces/governance/IGovernanceUpgrade.md)
        * [IGovernanceVoting](contracts/api/governance/interfaces/governance/IGovernanceVoting.md)
    * Libraries
      * [GovernanceActionLib](contracts/api/governance/libraries/GovernanceActionLib.md)
    * Mixins
      * [MixinAbstract](contracts/api/governance/mixins/MixinAbstract.md)
      * [MixinConstants](contracts/api/governance/mixins/MixinConstants.md)
      * [MixinCrosschain](contracts/api/governance/mixins/MixinCrosschain.md)
      * [MixinImmutables](contracts/api/governance/mixins/MixinImmutables.md)
      * [MixinInitializer](contracts/api/governance/mixins/MixinInitializer.md)
      * [MixinState](contracts/api/governance/mixins/MixinState.md)
      * [MixinStorage](contracts/api/governance/mixins/MixinStorage.md)
      * [MixinUpgrade](contracts/api/governance/mixins/MixinUpgrade.md)
      * [MixinVoting](contracts/api/governance/mixins/MixinVoting.md)
    * Proxies
      * [RigoblockGovernanceFactory](contracts/api/governance/proxies/RigoblockGovernanceFactory.md)
      * [RigoblockGovernanceProxy](contracts/api/governance/proxies/RigoblockGovernanceProxy.md)
    * Strategies
      * [RigoblockGovernanceStrategy](contracts/api/governance/strategies/RigoblockGovernanceStrategy.md)
  * Protocol
    * [IRigoblockV3Pool](contracts/api/protocol/IRigoblockV3Pool.md)
    * [ISmartPool](contracts/api/protocol/ISmartPool.md)
    * [SmartPool](contracts/api/protocol/SmartPool.md)
    * Core
      * Actions
        * [MixinActions](contracts/api/protocol/core/actions/MixinActions.md)
        * [MixinOwnerActions](contracts/api/protocol/core/actions/MixinOwnerActions.md)
      * Immutable
        * [MixinConstants](contracts/api/protocol/core/immutable/MixinConstants.md)
        * [MixinImmutables](contracts/api/protocol/core/immutable/MixinImmutables.md)
        * [MixinStorage](contracts/api/protocol/core/immutable/MixinStorage.md)
      * State
        * [MixinPoolState](contracts/api/protocol/core/state/MixinPoolState.md)
        * [MixinPoolValue](contracts/api/protocol/core/state/MixinPoolValue.md)
        * [MixinStorageAccessible](contracts/api/protocol/core/state/MixinStorageAccessible.md)
      * Sys
        * [MixinFallback](contracts/api/protocol/core/sys/MixinFallback.md)
        * [MixinInitializer](contracts/api/protocol/core/sys/MixinInitializer.md)
    * Deps
      * [Authority](contracts/api/protocol/deps/Authority.md)
      * [Escrow](contracts/api/protocol/deps/Escrow.md)
      * [ExtensionsMap](contracts/api/protocol/deps/ExtensionsMap.md)
      * [ExtensionsMapDeployer](contracts/api/protocol/deps/ExtensionsMapDeployer.md)
      * [PoolRegistry](contracts/api/protocol/deps/PoolRegistry.md)
    * Extensions
      * [EApps](contracts/api/protocol/extensions/EApps.md)
      * [ECrosschain](contracts/api/protocol/extensions/ECrosschain.md)
      * [EERC20](contracts/api/protocol/extensions/EERC20.md)
      * [EGmxCallback](contracts/api/protocol/extensions/EGmxCallback.md)
      * [ENavView](contracts/api/protocol/extensions/ENavView.md)
      * [EOracle](contracts/api/protocol/extensions/EOracle.md)
      * [EUpgrade](contracts/api/protocol/extensions/EUpgrade.md)
      * Adapters
        * [A0xRouter](contracts/api/protocol/extensions/adapters/A0xRouter.md)
        * [AGmxV2](contracts/api/protocol/extensions/adapters/AGmxV2.md)
        * [AGovernance](contracts/api/protocol/extensions/adapters/AGovernance.md)
        * [AHyperliquid](contracts/api/protocol/extensions/adapters/AHyperliquid.md)
        * [AIntents](contracts/api/protocol/extensions/adapters/AIntents.md)
        * [AMulticall](contracts/api/protocol/extensions/adapters/AMulticall.md)
        * [AStaking](contracts/api/protocol/extensions/adapters/AStaking.md)
        * [AUniswap](contracts/api/protocol/extensions/adapters/AUniswap.md)
        * [AUniswapDecoder](contracts/api/protocol/extensions/adapters/AUniswapDecoder.md)
        * [AUniswapRouter](contracts/api/protocol/extensions/adapters/AUniswapRouter.md)
        * [IPermit2Forwarder](contracts/api/protocol/extensions/adapters/IPermit2Forwarder.md)
        * [IUniswapRouter](contracts/api/protocol/extensions/adapters/IUniswapRouter.md)
        * Interfaces
          * [IA0xRouter](contracts/api/protocol/extensions/adapters/interfaces/IA0xRouter.md)
          * [IAGmxV2](contracts/api/protocol/extensions/adapters/interfaces/IAGmxV2.md)
          * [IAGovernance](contracts/api/protocol/extensions/adapters/interfaces/IAGovernance.md)
          * [IAHyperliquid](contracts/api/protocol/extensions/adapters/interfaces/IAHyperliquid.md)
          * [IAIntents](contracts/api/protocol/extensions/adapters/interfaces/IAIntents.md)
          * [IAMulticall](contracts/api/protocol/extensions/adapters/interfaces/IAMulticall.md)
          * [IAStaking](contracts/api/protocol/extensions/adapters/interfaces/IAStaking.md)
          * [IAUniswap](contracts/api/protocol/extensions/adapters/interfaces/IAUniswap.md)
          * [IAUniswapRouter](contracts/api/protocol/extensions/adapters/interfaces/IAUniswapRouter.md)
          * [IEApps](contracts/api/protocol/extensions/adapters/interfaces/IEApps.md)
          * [IECrosschain](contracts/api/protocol/extensions/adapters/interfaces/IECrosschain.md)
          * [IEERC20](contracts/api/protocol/extensions/adapters/interfaces/IEERC20.md)
          * [IEGmxCallback](contracts/api/protocol/extensions/adapters/interfaces/IEGmxCallback.md)
          * [IENavView](contracts/api/protocol/extensions/adapters/interfaces/IENavView.md)
          * [IEOracle](contracts/api/protocol/extensions/adapters/interfaces/IEOracle.md)
          * [IEUpgrade](contracts/api/protocol/extensions/adapters/interfaces/IEUpgrade.md)
          * [IMinimumVersion](contracts/api/protocol/extensions/adapters/interfaces/IMinimumVersion.md)
          * [IRigoblockExtensions](contracts/api/protocol/extensions/adapters/interfaces/IRigoblockExtensions.md)
    * Interfaces
      * [IAcrossSpokePool](contracts/api/protocol/interfaces/IAcrossSpokePool.md)
      * [IAuthority](contracts/api/protocol/interfaces/IAuthority.md)
      * [IERC20](contracts/api/protocol/interfaces/IERC20.md)
      * [IExtensionsMap](contracts/api/protocol/interfaces/IExtensionsMap.md)
      * [IExtensionsMapDeployer](contracts/api/protocol/interfaces/IExtensionsMapDeployer.md)
      * [IKyc](contracts/api/protocol/interfaces/IKyc.md)
      * [IMulticallHandler](contracts/api/protocol/interfaces/IMulticallHandler.md)
      * [IOracle](contracts/api/protocol/interfaces/IOracle.md)
      * [IPoolRegistry](contracts/api/protocol/interfaces/IPoolRegistry.md)
      * [IRigoblockPoolExtended](contracts/api/protocol/interfaces/IRigoblockPoolExtended.md)
      * [IRigoblockPoolProxy](contracts/api/protocol/interfaces/IRigoblockPoolProxy.md)
      * [IRigoblockPoolProxyFactory](contracts/api/protocol/interfaces/IRigoblockPoolProxyFactory.md)
      * [IWETH9](contracts/api/protocol/interfaces/IWETH9.md)
      * Pool
        * [IRigoblockV3PoolActions](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolActions.md)
        * [IRigoblockV3PoolEvents](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolEvents.md)
        * [IRigoblockV3PoolFallback](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolFallback.md)
        * [IRigoblockV3PoolImmutable](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolImmutable.md)
        * [IRigoblockV3PoolInitializer](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolInitializer.md)
        * [IRigoblockV3PoolOwnerActions](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolOwnerActions.md)
        * [IRigoblockV3PoolState](contracts/api/protocol/interfaces/pool/IRigoblockV3PoolState.md)
        * [IStorageAccessible](contracts/api/protocol/interfaces/pool/IStorageAccessible.md)
      * V4
        * Pool
          * [ISmartPoolActions](contracts/api/protocol/interfaces/v4/pool/ISmartPoolActions.md)
          * [ISmartPoolEvents](contracts/api/protocol/interfaces/v4/pool/ISmartPoolEvents.md)
          * [ISmartPoolFallback](contracts/api/protocol/interfaces/v4/pool/ISmartPoolFallback.md)
          * [ISmartPoolImmutable](contracts/api/protocol/interfaces/v4/pool/ISmartPoolImmutable.md)
          * [ISmartPoolInitializer](contracts/api/protocol/interfaces/v4/pool/ISmartPoolInitializer.md)
          * [ISmartPoolOwnerActions](contracts/api/protocol/interfaces/v4/pool/ISmartPoolOwnerActions.md)
          * [ISmartPoolState](contracts/api/protocol/interfaces/v4/pool/ISmartPoolState.md)
          * [IStorageAccessible](contracts/api/protocol/interfaces/v4/pool/IStorageAccessible.md)
    * Libraries
      * [ApplicationsLib](contracts/api/protocol/libraries/ApplicationsLib.md)
      * [CrosschainLib](contracts/api/protocol/libraries/CrosschainLib.md)
      * [DelegationLib](contracts/api/protocol/libraries/DelegationLib.md)
      * [EnumerableSet](contracts/api/protocol/libraries/EnumerableSet.md)
      * [EscrowFactory](contracts/api/protocol/libraries/EscrowFactory.md)
      * [GmxAdapterLib](contracts/api/protocol/libraries/GmxAdapterLib.md)
      * [GmxCallbackLib](contracts/api/protocol/libraries/GmxCallbackLib.md)
      * [GmxLib](contracts/api/protocol/libraries/GmxLib.md)
      * [HyperliquidLib](contracts/api/protocol/libraries/HyperliquidLib.md)
      * [NavImpactLib](contracts/api/protocol/libraries/NavImpactLib.md)
      * [NavView](contracts/api/protocol/libraries/NavView.md)
      * [ReentrancyGuardTransient](contracts/api/protocol/libraries/ReentrancyGuardTransient.md)
      * [SafeTransferLib](contracts/api/protocol/libraries/SafeTransferLib.md)
      * [SlotDerivation](contracts/api/protocol/libraries/SlotDerivation.md)
      * [StorageLib](contracts/api/protocol/libraries/StorageLib.md)
      * [StorageSlot](contracts/api/protocol/libraries/StorageSlot.md)
      * [TransientSlot](contracts/api/protocol/libraries/TransientSlot.md)
      * [TransientStorage](contracts/api/protocol/libraries/TransientStorage.md)
      * [VersionLib](contracts/api/protocol/libraries/VersionLib.md)
      * [VirtualStorageLib](contracts/api/protocol/libraries/VirtualStorageLib.md)
    * Proxies
      * [RigoblockPoolProxy](contracts/api/protocol/proxies/RigoblockPoolProxy.md)
      * [RigoblockPoolProxyFactory](contracts/api/protocol/proxies/RigoblockPoolProxyFactory.md)
    * Types
      * [CrosschainTokens](contracts/api/protocol/types/CrosschainTokens.md)
      * [GmxClaimableHelpers](contracts/api/protocol/types/GmxClaimableHelpers.md)
      * [GmxFallback](contracts/api/protocol/types/GmxFallback.md)
  * RigoToken
    * Inflation
      * [Inflation](contracts/api/rigoToken/inflation/Inflation.md)
      * [InflationL2](contracts/api/rigoToken/inflation/InflationL2.md)
    * Interfaces
      * [IInflation](contracts/api/rigoToken/interfaces/IInflation.md)
      * [IProofOfPerformance](contracts/api/rigoToken/interfaces/IProofOfPerformance.md)
      * [IRigoToken](contracts/api/rigoToken/interfaces/IRigoToken.md)
    * ProofOfPerformance
      * [ProofOfPerformance](contracts/api/rigoToken/proofOfPerformance/ProofOfPerformance.md)
    * RigoToken
      * [RigoToken](contracts/api/rigoToken/rigoToken/RigoToken.md)
  * Staking
    * [GrgVault](contracts/api/staking/GrgVault.md)
    * [Staking](contracts/api/staking/Staking.md)
    * [StakingProxy](contracts/api/staking/StakingProxy.md)
    * Immutable
      * [MixinConstants](contracts/api/staking/immutable/MixinConstants.md)
      * [MixinDeploymentConstants](contracts/api/staking/immutable/MixinDeploymentConstants.md)
      * [MixinStorage](contracts/api/staking/immutable/MixinStorage.md)
    * Interfaces
      * [IGrgVault](contracts/api/staking/interfaces/IGrgVault.md)
      * [IStaking](contracts/api/staking/interfaces/IStaking.md)
      * [IStakingEvents](contracts/api/staking/interfaces/IStakingEvents.md)
      * [IStakingProxy](contracts/api/staking/interfaces/IStakingProxy.md)
      * [IStorage](contracts/api/staking/interfaces/IStorage.md)
      * [IStorageInit](contracts/api/staking/interfaces/IStorageInit.md)
      * [IStructs](contracts/api/staking/interfaces/IStructs.md)
    * Libs
      * [LibCobbDouglas](contracts/api/staking/libs/LibCobbDouglas.md)
      * [LibFixedMath](contracts/api/staking/libs/LibFixedMath.md)
      * [LibSafeDowncast](contracts/api/staking/libs/LibSafeDowncast.md)
    * Rewards
      * [MixinPopManager](contracts/api/staking/rewards/MixinPopManager.md)
      * [MixinPopRewards](contracts/api/staking/rewards/MixinPopRewards.md)
    * Stake
      * [MixinStake](contracts/api/staking/stake/MixinStake.md)
      * [MixinStakeBalances](contracts/api/staking/stake/MixinStakeBalances.md)
      * [MixinStakeStorage](contracts/api/staking/stake/MixinStakeStorage.md)
    * Staking_pools
      * [MixinCumulativeRewards](contracts/api/staking/staking_pools/MixinCumulativeRewards.md)
      * [MixinStakingPool](contracts/api/staking/staking_pools/MixinStakingPool.md)
      * [MixinStakingPoolRewards](contracts/api/staking/staking_pools/MixinStakingPoolRewards.md)
    * Sys
      * [MixinAbstract](contracts/api/staking/sys/MixinAbstract.md)
      * [MixinFinalizer](contracts/api/staking/sys/MixinFinalizer.md)
      * [MixinParams](contracts/api/staking/sys/MixinParams.md)
      * [MixinScheduler](contracts/api/staking/sys/MixinScheduler.md)
  * Tokens
    * ERC20
      * [ERC20](contracts/api/tokens/ERC20/ERC20.md)
      * [IERC20](contracts/api/tokens/ERC20/IERC20.md)
    * UnlimitedAllowanceToken
      * [UnlimitedAllowanceToken](contracts/api/tokens/UnlimitedAllowanceToken/UnlimitedAllowanceToken.md)
    * WETH9
      * [WETH9](contracts/api/tokens/WETH9/WETH9.md)
  * Utils
    * 0xUtils
      * [Authorizable](contracts/api/utils/0xUtils/Authorizable.md)
      * [IAssetData](contracts/api/utils/0xUtils/IAssetData.md)
      * [IAssetProxy](contracts/api/utils/0xUtils/IAssetProxy.md)
      * [IERC20Token](contracts/api/utils/0xUtils/IERC20Token.md)
      * [IEtherToken](contracts/api/utils/0xUtils/IEtherToken.md)
      * [LibFractions](contracts/api/utils/0xUtils/LibFractions.md)
      * [LibMath](contracts/api/utils/0xUtils/LibMath.md)
      * [Ownable](contracts/api/utils/0xUtils/Ownable.md)
      * ERC20Proxy
        * [ERC20Proxy](contracts/api/utils/0xUtils/ERC20Proxy/ERC20Proxy.md)
        * [MAuthorizable](contracts/api/utils/0xUtils/ERC20Proxy/MAuthorizable.md)
        * [MixinAuthorizable](contracts/api/utils/0xUtils/ERC20Proxy/MixinAuthorizable.md)
      * Interfaces
        * [IAuthorizable](contracts/api/utils/0xUtils/interfaces/IAuthorizable.md)
        * [IOwnable](contracts/api/utils/0xUtils/interfaces/IOwnable.md)
    * Exchanges
      * Uniswap
        * INonfungiblePositionManager
          * [INonfungiblePositionManager](contracts/api/utils/exchanges/uniswap/INonfungiblePositionManager/INonfungiblePositionManager.md)
        * V3-periphery
          * Contracts
            * Interfaces
              * [IPeripheryImmutableState](contracts/api/utils/exchanges/uniswap/v3-periphery/contracts/interfaces/IPeripheryImmutableState.md)
              * [IPoolInitializer](contracts/api/utils/exchanges/uniswap/v3-periphery/contracts/interfaces/IPoolInitializer.md)
              * External
                * [IERC721](contracts/api/utils/exchanges/uniswap/v3-periphery/contracts/interfaces/external/IERC721.md)
    * LibSanitize
      * [LibSanitize](contracts/api/utils/libSanitize/LibSanitize.md)
    * Owned
      * [IOwnedUninitialized](contracts/api/utils/owned/IOwnedUninitialized.md)
      * [OwnedUninitialized](contracts/api/utils/owned/OwnedUninitialized.md)
<!-- AUTO-GENERATED-API-END -->
