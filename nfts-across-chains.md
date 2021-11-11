# Ethereum, Polygon and other EVM chains

NFT's are minted in contracts conforming to the [ERC721 specification](https://eips.ethereum.org/EIPS/eip-721).

Fractionalized NFT's follow the [ERC115 specification](https://eips.ethereum.org/EIPS/eip-1155).

NFT's are minted inside their contract and identified by an integer. These NFT's can be addressed using [Cermaic's NFT DID resolver](https://github.com/ceramicnetwork/nft-did-resolver#did-specs).

Each NFT has a `tokenURI` property that is, according to the specification, a URI to the token's "metadata" which is assumed to be a JSON file.

## Known Issues

* tokenURI is not a URI
* tokenURI is larger than a reasonable primaryKey
* tokenURI is an HTTP/HTTPS URL
  * rug pulls
  * server is down, service goes out of business

# Solana

