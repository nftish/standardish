# Known Cross-Chain Issues

* [tokenURI is not a URI](https://github.com/nftstorage/standardish/issues/1)

# Ethereum, Polygon and other EVM chains

NFT's are minted in contracts conforming to the [ERC721 specification](https://eips.ethereum.org/EIPS/eip-721).

Fractionalized NFT's follow the [ERC115 specification](https://eips.ethereum.org/EIPS/eip-1155).

NFT's are minted inside their contract and identified by an integer. These NFT's can be addressed using [Cermaic's NFT DID resolver](https://github.com/ceramicnetwork/nft-did-resolver#did-specs).

Each NFT has a `tokenURI` property that is, according to the specification, a URI to the token's "metadata" which is assumed to be a JSON file.

There's another community [working group](https://www.nftstandards.wtf/NFT+Standards+Wiki+-+READ.me) focused on Ethereum related NFT issues.

## Known Issues

* [tokenURI is larger than a reasonable primaryKey](https://github.com/nftstorage/standardish/issues/2)
* [tokenURI is an HTTP/HTTPS URL](https://github.com/nftstorage/standardish/issues/3)
  * [rugpulls](https://github.com/nftstorage/standardish/issues/4)

# Solana

In Solana, contracts don't mutate *their own* state, they mutate state within an "account." As such, Solana NFT's are **NOT** idenfiable as an integer (or other identifier) *within* a particular contract.

[`spl-token` provides the base interface](https://spl.solana.com/token) for all token programs (similar to ERC20). NFT's in Solana are spl-tokens
that are [capped to a supply of "1."](https://www.zappycode.com/tutorials/create-your-own-token-and-nft-on-solana)

Most NFT's in Solana use [Metaplex](https://metaplex.com), or a contract derived from Metaplex. Metaplex has [written a clear standard](https://docs.metaplex.com/nft-standard) for how to express metadata.json and has also defines additional metadata properties.

NFT's use a mix of [on-chain and off-chain metadata](https://github.com/nftstorage/standardish/blob/main/metadata-json.md#metaplex-expanded-metadata-definition).

# Flow

Flow was built with NFT's in mind.

In Cadence (Flow's Smart Contract Language), each NFT is represented by a [resource](https://medium.com/dapperlabs/resource-oriented-programming-bee4d69c8f8e) with an integer ID. [That resource object is stored in a user's account](https://docs.onflow.org/cadence/tutorial/04-non-fungible-tokens/).

Cadence has many features for working with NFT's detailed in the [Flow NFT Spec](https://github.com/onflow/flow-nft).

Typically, metadata is stored off-chain but there [are efforts to move that on-chain](https://github.com/onflow/flow-nft/issues/9).
