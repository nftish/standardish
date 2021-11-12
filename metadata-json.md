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

* metadata.json: videos in the image field

## Visible but by no means universal adoption of...

### properties field for "arbitrary properties"

[ERC1155]() tried to reign in arbitrary property extensions by providing the following additional schema.

```JSON
        "properties": {
            "type": "object",
            "description": "Arbitrary properties. Values may be strings, numbers, object or arrays."
        }
```
