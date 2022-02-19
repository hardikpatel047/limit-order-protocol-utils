# Utils library for Onlyswap Limit Orders Protocol

This is the package of utilities for working with the `Onlyswap Limit Orders Protocol`

## Installation

### Node

```
npm install limit-order-protocol
```

### Yarn

```
yarn add limit-order-protocol
```

---

## About

Contract allows users to place limit orders, that later could be filled on-chain. Limit order itself is a data structure created off-chain and signed according to EIP-712.

Key features of the protocol is extreme flexibility and high gas efficiency that achieved by using following order types.

## I. Limit order

A limit order is a financial instrument with which you can put up an ERC-20 token for sale at a fixed price.  
For example, you can put up for sale 2 WBTC tokens at the price of 82415 DAI tokens.

Onlyswap limit orders protocol has many tools for flexible trade management:

-   Partial fill
-   Predicates
-   Single cancellation
-   Bunch cancellation
-   Fullness check
-   Validation

> **Note:** You can create a limit order even if your balance is insufficient to execute the limit order right now. However you must have an allowance for the maker asset.