# How the DEX works

Technically there are two main components. 

- The order book - Contains all the signed orders (the NFTs which can be sold). The order book is off-chain.
- The DEX smart contract - Exchanges the assets in a single transaction.

## NFT Owner sells his NFT

![DEX3 How the DEX works](img/om-how-it-works.jpg)

The order book contains all the signed orders from the sellers (aka makers). Whenever someone wants to sell an NFT, the seller defines a fix price and the currency to pay with. After the seller creates a digital signature with his crypto wallet. This signed order will then be stored in the order book. 

The buyer (aka taker) will select the signed order and submit this order to the DEX smart contract. The DEX smart contracts will validate the order (signature, price match, and so on). If the order and signature is valid the DEX smart contract will exchange the assets in a decentralized way in a single transaction.

## Transaction analysis

| Description     | Address                                    |
| --------------- | ------------------------------------------ |
| Dex Address     | 0x6a85796b158729474150d1c94a66184368d52142 |
| Dex Operator    | 0x7c368f7d21503a1857c1b885470b330f5d26c4b7 |
| WETH Address    | 0xb4fbf271143f4fbf7b91a5ded31805e42b2208d6 |
| User1 - Seller | 0x92e56418297664a34a91f0e3a6a81aa092f268f1 |
| User2 - Buyer    | 0x0291170dd80c24f2059ca0ad840f3d6573a7a46b |

### Sell ERC721 NFT with ETH

User1 creates a sell order. 

```json
{  
  "hash": "0x30ba20598b4e977f26465c25f7ba7bd6f4724924ae28cd3b81f67627ce323786",  
  "sig": "0x3f89a18f83ca12b65c94394f50ff9c7107bee18d4d22c1f067a4558c6b51f0213b38e2791042fab700c75560295bf40236f66a4efb2e2428933613867977c6d71c",  
  "order": {  
    "maker": "0x92e56418297664a34a91f0e3a6a81aa092f268f1",  
    "nftAddress": "0xec455e43adf3b073d9fef311205305ccf8e7574a",  
    "nftTokenId": "8680783491275350067",  
    "orderType": 0,  
    "maxNbrOfNftsToTrade": "1",  
    "erc20PaymentToken": "0x0000000000000000000000000000000000000000",  
    "pricePerNft": "1000000000000000",  
    "ttl": 1667329052257,  
    "nonce": 4914140582696146000  
  }  
}
```

User2 fills the order.

TX Hash: [0x56e80bb136c9d4ac4e9ff9b54e3c8879b785b49cf4e58d3ba8c15e4ba96c49fa](https://goerli.etherscan.io/tx/0x56e80bb136c9d4ac4e9ff9b54e3c8879b785b49cf4e58d3ba8c15e4ba96c49fa)

### Sell ERC721 NFT with WETH

User1 creates a sell order.
```json
{  
  "hash": "0xfb997896b8bb7e5a43e9588037bb27a2b36e27a3033dcf9d659a3eee0a069cff",  
  "sig": "0xfe3fb89ceb9e5ba82b9085b298f81cf8c15e13ef6a9b42326c225c2ded066a5137c9930044ae5831f507f74c1b096eb267ed33055ba895097f8bb0ee6d023a9d1b",  
  "order": {  
    "maker": "0x92e56418297664a34a91f0e3a6a81aa092f268f1",  
    "nftAddress": "0xec455e43adf3b073d9fef311205305ccf8e7574a",  
    "nftTokenId": "1773901249514399562",  
    "orderType": 0,  
    "maxNbrOfNftsToTrade": "1",  
    "erc20PaymentToken": "0xb4fbf271143f4fbf7b91a5ded31805e42b2208d6",  
    "pricePerNft": "1000000000000000",  
    "ttl": 1667329561805,  
    "nonce": 142845367006028510  
  }  
}
```

User2 fills the order.
TX Hash: [0xc9ea8a7529bdddcf67976d2615905fd16111575993662cec0f70363c5ae689bc](https://goerli.etherscan.io/tx/0xc9ea8a7529bdddcf67976d2615905fd16111575993662cec0f70363c5ae689bc)

### Bid for ERC721 with WETH
User2 wants to buy the NFT but there is no sell order. Therefor the User2 creates a bid order

```json
{  
  "hash": "0xc0ed952de9a275d374dc0dc544b9b8f5fe1eca24ae6d6f62eb0e67361f5f53b2",  
  "sig": "0x0b797e630d6a5c9c6e17c06c78b1bf28d1a6e40828e9b47543ebeb27432249d34d04ca4dccc19f92bf615cb0b7f72957ab7d994fb9d6b2cd91f3b1c0745e2d5d1c",  
  "order": {  
    "maker": "0x0291170dd80c24f2059ca0ad840f3d6573a7a46b",  
    "nftAddress": "0xec455e43adf3b073d9fef311205305ccf8e7574a",  
    "nftTokenId": "5240129628470187580",  
    "orderType": 2,  
    "maxNbrOfNftsToTrade": "1",  
    "erc20PaymentToken": "0xb4fbf271143f4fbf7b91a5ded31805e42b2208d6",  
    "pricePerNft": "1000000000000000",  
    "ttl": 1667329785478,  
    "nonce": 7758329145365391000  
  }  
}
```

User1 fills the order.
TX Hash: [0x01972a7704bfffba713881b30bedb044fcb734a75a9193d1c7c975170f9526ae](https://goerli.etherscan.io/tx/0x01972a7704bfffba713881b30bedb044fcb734a75a9193d1c7c975170f9526ae)
