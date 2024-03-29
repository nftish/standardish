# metadata.json

By convention, NFT's across different chains link to JSON encoded metadata.

Some chains put this data on-chain, some link to this data off-chain. Regardless of where this data lives, a defacto-standard for
how this metadata is structured has emerged.

Since this metadata is rarely validated in order for an NFT to be minted there is never 100% compliance.

## Nearly universal adoption of...

### name, description, image

[ERC721](https://eips.ethereum.org/EIPS/eip-721) provides the following schema for "Asset Metadata." These are
by far the most commonly adopted properties.

```JSON
{
    "title": "Asset Metadata",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "description": "Identifies the asset to which this NFT represents"
        },
        "description": {
            "type": "string",
            "description": "Describes the asset to which this NFT represents"
        },
        "image": {
            "type": "string",
            "description": "A URI pointing to a resource with mime type image/* representing the asset to which this NFT represents. Consider making any images at a width between 320 and 1080 pixels and aspect ratio between 1.91:1 and 4:5 inclusive."
        }
    }
}
```

#### Known Issues

* [metadata.json: videos in the image field](https://github.com/nftstorage/standardish/issues/5)

## Visible but by no means universal adoption of...

### properties field for "arbitrary properties"

[ERC1155]() tried to reign in arbitrary property extensions by providing the following additional schema.

```JSON
        "properties": {
            "type": "object",
            "description": "Arbitrary properties. Values may be strings, numbers, object or arrays."
        }
```

### Metaplex expanded metadata definition

Most NFT's in Solana follow the Metaplex [standard for metadata](https://docs.metaplex.com/nft-standard) which includes some expanded property definitions and also specifies some metadata properties that live on-chain.

"Basic info about the SPL token is provided with the Metadata struct, whose account address is a PDA with a derived key of ['metadata', metadata_program_id, mint_id]."

Developers are instructed to rely on the following on-chain metadata:

| Field                   | Type    | Description                                                    | How do we display it                                                                                    |
| ----------------------- | ------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| name                    | string  | name of the asset                                              | grid view and single NFT view                                                                           |
| symbol                  | string  | symbol of the asset                                            | not shown currently                                                                                     |
| uri                     | string  | URI to the external JSON representing the asset                | linked in the single NFT view                                                                           |
| creators                | array   | public key of each creator                                     | shown in the single NFT view, resolved to twitter handles if they are connected via Solana Name Service |
| update_authority        | string  | public key of the metadata owner                               | shown in the single NFT view, can be updated in the send NFT modal                                      |
| primary_sale_happened   | boolean | flag describing whether the primary sale of the token happened | visible in the send NFT modal, can be updated                                                           |
| seller_fee_basis_points | number  | royalties percentage awarded to creators                       | shown as a percentage received by each co-creator                                                       |

Off-chain metadata is referenced via the `uri` field and the spec contains the following additional property definitions:

```JSON
{
  "name": "Solflare X NFT",
  "symbol": "",
  "description": "Celebratory Solflare NFT for the Solflare X launch",
  "seller_fee_basis_points": 0,
  "image": "https://www.arweave.net/abcd5678?ext=png",
  "animation_url": "https://www.arweave.net/efgh1234?ext=mp4",
  "external_url": "https://solflare.com",
  "attributes": [
    {
      "trait_type": "web",
      "value": "yes"
    },
    {
      "trait_type": "mobile",
      "value": "yes"
   },
   {
      "trait_type": "extension",
      "value": "yes"
    }
  ],
  "collection": {
     "name": "Solflare X NFT",
     "family": "Solflare"
  },
  "properties": {
    "files": [
      {
        "uri": "https://www.arweave.net/abcd5678?ext=png",
        "type": "image/png"
      },
      {
        "uri": "https://watch.videodelivery.net/9876jkl",
        "type": "unknown",
        "cdn": true
      },
      {
        "uri": "https://www.arweave.net/efgh1234?ext=mp4",
        "type": "video/mp4"
      }
    ],
    "category": "video",
    "creators": [
      {
        "address": "SOLFLR15asd9d21325bsadythp547912501b",
        "share": 100
      }
    ]
  }
}
```
