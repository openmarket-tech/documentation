# Client / Frontend integration
In this chapter we cover how a client (Web-frontend or backend) can create and sign an order.

## Structure of an order

Example signed order.
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

| Property            | Description                                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------------------- |
| maker               | The one who created and signed the order                                                                      |
| nftAddress          | The NFT smart contract address (ERC721, ERC1155)                                                              |
| nftTokenId          | The NFT tokenId                                                                                               |
| orderType           | 0: SELL_ERC721, 1: SELL_ERC1155, 2: BID_FOR_ERC721, 3: BID_FOR_ERC1155                                        |
| maxNbrOfNftsToTrade | In case of ERC721: Must be 1. In case of ERC1155: Must be 1..n.                                               |
| erc20PaymentToken   | The ERC20 token required to fill this order. If address is 0x0 then it's an Ether payment                     |
| pricePerNft         | Price for a single NFT. For ERC721 it's the price. For ERC1155 multiply with amount the buyer wants to trade. |
| ttl                 | Unixtimestamp in seconds. How long the order is valid                                                         |
| nonce | Unique nonce. Clients must always create a new unique nonce. This is a security feature |


## Create the hash
The hash is a `keccak256` over all the properties of the order. To create this hash the most simple way is to call the DEX smart contract `createMakerHash` function.

```Solidity
function createMakerHash(
	address payable maker,
	address nftAddress,
	uint256 nftTokenId,
	OrderType orderType,
	uint256 maxNbrOfNftsToTrade,
	address erc20PaymentToken,
	uint256 pricePerNft,
	uint256 ttl,
	uint256 nonce
) external pure returns (bytes32)
```

This function returns a `bytes32` which represents the hash. 

In JavaScript this could look like this:
```js
// Returns Promise
createMakerHash(order) {
	console.dir("Create Maker Hash:", order);
	var dex3 = this.getDex3Instance();
	return dex3.methods.createMakerHash(
		order.maker,
		order.nftAddress,
		order.nftTokenId,
		order.orderType,
		order.maxNbrOfNftsToTrade,
		order.erc20PaymentToken,
		order.pricePerNft,
		order.ttl,
		order.nonce
	).call();
}
```

### Create the signature

#### Using JavaScript with Web3js 
```js
web3.eth.personal.sign(hash, usersAddress);
```

It's important to use the `web3.personal.sign` function. See [web3js doc](https://web3js.readthedocs.io/en/v1.2.11/web3-eth-personal.html#sign)

#### Using Java with Web3j

```java
public static String sign(Credentials credentials, String hash) {  
    byte[] hashBytes = HexUtil.fromHexString(hash);  
    Sign.SignatureData sd = Sign.signPrefixedMessage(hashBytes, credentials.getEcKeyPair());  
    return SignatureDataToHexString(sd);  
}  
  
public static String SignatureDataToHexString(Sign.SignatureData sd) {  
    byte[] subrRev = Arrays.copyOfRange(sd.getR(), 0, 32);  
    byte[] subsRev = Arrays.copyOfRange(sd.getS(), 0, 32);  
    byte[] result = new byte[65];  
    for (int i = 0; i < 32; i++) {  
        result[i] = subrRev[i];  
    }  
  
    for (int i = 0; i < 32; i++) {  
        result[i + 32] = subsRev[i];  
    }  
  
    result[64] = sd.getV()[0];  
  
    return HexUtil.toHexString0xPrefix(result);  
}
```