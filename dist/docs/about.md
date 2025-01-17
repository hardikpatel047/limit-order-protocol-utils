<p align="center">
  <img src="https://app.1inch.io/assets/images/logo.svg" width="200" alt="1inch network" />
</p>

# Onlyswap limit order protocol

Onlyswap limit order protocol is a set of smart contracts, that can work on any EVM based blockchains (Ethereum, Binance Smart Chain, Polygon, etc.). Key features of the protocol is **extreme flexibility** and high **gas efficiency** that achieved by using two different order types - regular _Limit Order_ and _RFQ Order_.

Smart Contract allows users to place limit orders and RFQ Orders, that later could be filled on-chain.
Both type of orders is a data structure created off-chain and signed according to [EIP-712](https://eips.ethereum.org/EIPS/eip-712).

## Order types

#### Limit Order

1inch users can place their limit orders via 1inch [dApp](https://app.1inch.io/#/1/limit-order/WETH/DAI).
Anyone can fetch this signed orders using REST API endpoint ([Ethereum](https://limit-orders.1inch.exchange/swagger/ethereum/), [BSC](https://limit-orders.1inch.exchange/swagger/binance/), [Polygon](https://limit-orders.1inch.exchange/swagger/polygon/)) to perform trade by filling order on-chain.
To do that he or she pass signed order to the `fillOrder` method on the contract ([Ethereum](https://etherscan.io/address/0x3ef51736315f52d568d6d2cf289419b9cfffe782), [BSC](https://bscscan.com/address/0xe3456f4ee65e745a44ec3bcb83d0f2529d1b84eb), [Polygon](https://polygonscan.com/address/0xb707d89d29c189421163515c59e42147371d6857)).
_Note: trades buyer and seller should approve their asset to be used by 1inch limit order contract._

Pathfinder algorithm use limit orders placed via `dApp` and REST API, as a liquidity source, and make it available to fill to any 1inch user.
So, 1inch limit orders are integrated into the DeFi ecosystem from the day one.

Limit orders are extremely **flexible** limit order, can be configured with:

1. Order execution predicate.
    - Typical usage is checking that certain time stamp or block number. With this you can set certain expiration time.
    - You can specify construct any predicate that you want, for example check that certain price is higher than oracle price, to implement stop loss or take profit stategies
2. Helper function for asset price evaluation.
    - Function that will allow to extract assets price from arbitrary on-chain source
3. Callback, for to notify maker on order execution.

#### RFQ order

RFQ orders has different use case, and dedicated to market makers at first place. Typical scenario is following:
Market maker create a bunch of RFQ Orders, and expose it via API.
Trading or platform / algorithm ask market maker quotes, and if it match his needs, he receives signed RFQ order from market maker.

**Gas optimized order** with restricted capabilities suitable **for market makers**

-   Support expiration time
-   Support cancelation by order id
-   RFQ Order could be filled only once
-   Partial Fill is possible (once)

## More resources

-   You can use it right in [1inch dApp](https://app.1inch.io/#/1/limit-order/WETH/DAI)
-   Smart Contracts [repository](https://github.com/1inch/limit-order-protocol/)
-   Utils library [repository](https://github.com/1inch/limit-order-protocol-utils/)
-   REST API ([Ethereum](https://limit-orders.1inch.exchange/swagger/ethereum/), [BSC](https://limit-orders.1inch.exchange/swagger/binance/), [Polygon](https://limit-orders.1inch.exchange/swagger/polygon/))
