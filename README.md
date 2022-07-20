# Expanded NFTs

Based on the [Zora NFT Editions](https://github.com/ourzora/nft-editions) contracts.

## What are these contracts?

1. `ExpandedNFT`
   Each drop is a unique contract.
   This allows for easy royalty collection, clear ownership of the collection, and your own contract 🎉
2. `DropCreator`
   Gas-optimized factory contract allowing you to easily + for a low gas transaction create your own drop mintable contract.
3. `SharedNFTLogic`
   Contract that includes dynamic metadata generation for your editions removing the need for a centralized server.
   imageUrl and animationUrl can be base64-encoded data-uris for these contracts totally removing the need for IPFS

## How do I create a new edition?

call `createEdition` with the given arguments to create a new editions contract:

- Name: Token Name Symbol (shows in etherscan)
- Symbol: Symbol of the Token (shows in etherscan)
- Description: Description of the Token (shows in the NFT description)
- Animation URL: IPFS/Arweave URL of the animation (video, webpage, audio, etc)
- Animation Hash: sha-256 hash of the animation, 0x0 if no animation url provided
- Image URL: IPFS/Arweave URL of the image (image/, gifs are good for previewing images)
- Image Hash: sha-256 hash of the image, 0x0 if no image url provided
- Edition Size: Number of this edition, if set to 0 edition is not capped/limited
- VIP Mint Limit: Number of the edition a VIP can mint when minting is restricted to VIP
- Member Mint Limit: Number of the edition a member can mint when minting is restricted to members
- BPS Royalty: 500 = 5%, 1000 = 10%, so on and so forth, set to 0 for no on-chain royalty (not supported by all marketplaces)

## How do I sell/distribute editions?

Now that you have a edition, there are multiple options for lazy-minting and sales:

1. To sell editions for ETH you can call `setSalePrice`
2. To allow certain accounts to mint `setApprovedMinter(address, approved)`.
3. To mint yourself to a list of addresses you can call `mintEditions(addresses[])` to mint an edition to each address in the list.

## How do I create a new contract?

### Directly on the blockchain:

1. Find/Deploy the `DropCreator` contract
2. Call `createDrop` on the `DropCreator`

## Developing with these contracts

### Install

`yarn install`

### Test

`yarn test`

### Deploying:

(Replace network with desired network)

`yarn hardhat deploy --network rinkeby`

### Verifying:

`yarn hardhat sourcify --network rinkeby && hardhat etherscan-verify --network rinkeby`

## Deployed

### Rinkeby

- SharedNFTLogic [0x707d795e898c32ebff02d717d8798fc1126ba001](https://rinkeby.etherscan.io/address/0x707d795e898c32ebff02d717d8798fc1126ba001)
- ExpandedNFT [0x1e6444BF4efc10e916c08410E33E5B753f0A1815](https://rinkeby.etherscan.io/address/0x1e6444BF4efc10e916c08410E33E5B753f0A1815)
- DropCreator [0x9692a6E918B8B87F4a533697E40F765e148fF334](https://rinkeby.etherscan.io/address/0x9692a6E918B8B87F4a533697E40F765e148fF334)
