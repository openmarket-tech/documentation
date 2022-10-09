# OpenMarket Documentation

OpenMarket is an NFT marketplace. OpenMarket is built on three main modules:
-	Frontend: User can browse, filter, buy, and sell NFTs.
-	Backend: Indexing NFTs and the corresponding metadata. Keep track of the order book. Provides APIs for the frontend.
-	Smart-Contract / DEX: Buy trades relay only on blockchain technology. By buying NFTs the user directly interacts over a P2P network with the smart contract without a centralized party.

OpenMarket comes with two different flavors. The public instance and a white label instance. The white able instance is designed to run on the customers infrastructure or cloud service where the customer is in full control of all the components. This document focuses on the white label flavor.

## Core Features

### Smart Contract
- Works on all EVM based blockchains
- Supports sell- and bid-orders
- Swaps ERC-721 or ERC-1155 NFTs with native coin or ERC-20 Token
- Order validation
- Buying with native Coin (ETH, Matic, …)
- Buying with any ERC-20 Token
- Canceling orders
- 100% decentralized / Code is law

### Backend
- One instance works on all EVM based blockchains
- Indexing any ERC-721 / ERC-1155 NFT
- Configurable payment options
- Orderbook management
- Filtering NFTs and orders
- Fully configurable over admin APIs
- Runs on all cloud services (Docker)
- Requires only JSON-RPC, Etherscan API

### USPs
- Works on all EVM based blockchains. One Frontend/API for all.
- Minimal Gas usage. OpenMarket trades uses around 130k Gas (vs OpenSea 252k-360k Gas usage).
- OpenMarket.tech as a service for any NFT project.
- OpenMarket White-label. Independent and customized instance for customers/projects (licensed Source-Code or Binaries).
- Buying/Selling with the native Coin or any ERC-20 Token on the related blockchain. 
- Lightweight - Requires only JSON-RPC, Etherscan and MongoDB (no 3rd party vendor lock-in).
