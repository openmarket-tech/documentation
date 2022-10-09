# OpenMarket Documentation

OpenMarket is an NFT marketplace. OpenMarket is built on three main modules:
-	Frontend: User can browse, filter, buy, and sell NFTs.
-	Backend: Indexing NFTs and the corresponding metadata. Keep track of the order book. Provides APIs for the frontend.
-	Smart-Contract / DEX: Buy trades relay only on blockchain technology. By buying NFTs the user directly interacts over a P2P network with the smart contract without a centralized party.

OpenMarket comes with two different flavors. The public instance and a white label solution. OpenMarket white-label solution is an out-of-the-box NFT-Marketplace for trading NFTs. 
It’s highly customizable and can be adjusted for customer requirements. OpenMarket works technically on all EVM based blockchains. It’s designed to run on the customers cloud infrastructure and be operated by the customer. 

[Demonstration instance](https://openmarket.tech/#/)

## OpenMarket products

OpenMarket.tech

- Public and global accessible NFT marketplace
- Integrates several test and main nets
- Offers public APIs
- Multiple Blockchains connected

OpenMarket White-label

- Designed for customer projects
- Independent deployment on the customers cloud service or data center
- Fully customizable
- Customer is under control of everything (smart-contract, backend and frontend)
- We are selling source-code or binary lifetime software license.
- We provide customization.


## Core Features

OpenMarket is built on three main modules:

- Frontend: User can browse, filter, buy, and sell NFTs.
- Backend: Indexing NFTs and the corresponding metadata. Keep track of the order book. Provides APIs for the frontend.
- Smart-Contract / DEX: Buy trades relay only on blockchain technology. By buying NFTs the user directly interacts over a P2P network with the smart contract without a centralized party.

Supported interfaces:

- ERC-20
- ERC-721
- ERC-1155
- ERC-2981 (Royalty standard)

### Smart contract
- Works on all EVM based blockchains
- Swaps ERC-721 / ERC-1155 NFTs with native coin or ERC-20 Token
- Order validation
- Buying with native Coin (ETH, Matic, …)
- Buying with any ERC-20 Token
- Supports the ERC-2981 Royalty standard
- Cancelling orders
- 100% decentralized / Code is law

### Backend
- One instance works on all EVM based blockchains
- Indexing any ERC-721 / ERC-1155 NFT
- Configurable payment options
- Orderbook management
- Filtering NFTs and orders
- Fully configurable over admin APIs
- Runs on all cloud services (Docker)

### USPs
- Works on all EVM based blockchains. One Frontend/API for all.
- Minimal Gas usage. OpenMarket trades uses around 130k Gas (vs OpenSea 252k-360k Gas usage).
- OpenMarket.tech as a service for any NFT project.
- OpenMarket White-label. Independent and customized instance for customers/projects (licensed Source-Code or Binaries).
- Buying/Selling with the native Coin or any ERC-20 Token on the related blockchain. 
- Lightweight - Requires only JSON-RPC, Etherscan and MongoDB (no 3rd party vendor lock-in).
