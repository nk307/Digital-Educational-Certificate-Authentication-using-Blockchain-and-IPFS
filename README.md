# ipfs-image-dapp

## Overview

This is a decentralized application (dApp) that demonstrates how to implement IPFS file uploads and store the IPFS hash in an Ethereum smart contract.

IPFS and the Blockchain are a perfect match. Why? You can address large amounts of data with IPFS, and place the immutable, permanent IPFS links into a blockchain transaction. This will timestamp and secure your content, without having to put the data on the chain itself. You now have undisputable proof that your image existed at that time it was uploaded.

## Usage

### Main Page

In this application, the main page displays a list of images filtered by owner. Each image displays the image, title, description, tags, upload timestamp and IPFS hash.

![IPFS Image dApp](https://github.com/iwaldman/ipfs-image-dapp/blob/master/app.png?raw=true 'IPFS Image dApp')

### Upload an Image

Click *Upload Image* to upload an image to IPFS and the blockchain. You will are required to enter an image title, optional description and appropriate tags. Click *Upload* to submit.

![IPFS Image dApp](https://github.com/iwaldman/ipfs-image-dapp/blob/master/upload-image.png?raw=true 'IPFS Image dApp')

## Our stack

For this project, we used the following stack:

- Solidity Smart Contracts
- IPFS for storing image data via Infura
- Truffle and Ganache for our development and testing framework
- React / Redux / Bootstrap 4 for our front-end development
- MetaMask for our web3 provider
- OpenZeppelin library

## Pre-requisites

1.  You will need Metamask plugin for Chrome. While there are other options available, only Metamask is covered here.
2.  Make sure you have [Node.js](https://nodejs.org/en/) installed. If you run into trouble, this was created with `v10.1.0`.

## Installation

1.  Install [Truffle Framework](http://truffleframework.com/) and [Ganache CLI](http://truffleframework.com/ganache/) globally. If you prefer, the graphical version of Ganache works as well.

    ```bash
    npm install -g truffle
    npm install -g ganache-cli
    ```

2.  Run the development blockchain.

    ```bash
    // no blocktime specified so transaction will be mined instantly
    ganache-cli
    ```

    You may want to pass in a blocktime. Otherwise, it's difficult to track things like loading indicators because Ganache will mine instantly. I've noticed that using a blocktime while running `truffle test` causes issues.

    ```bash
    // 3 second blocktime
    ganache-cli -b 3
    ```

3.  Open another terminal, clone this repo and install its dependencies.

    ```bash
    git clone https://github.com/iwaldman/ipfs-image-dapp.git

    cd ipfs-image-dapp

    npm install
    ```

    - If you get an error on install, don't panic. It should still work.

4.  Compile and migrate the smart contracts.

    ```bash
    truffle compile

    truffle migrate
    ```

5.  Start the application

    ```bash
    npm run start
    ```

6.  Navigate to http://localhost:3000/ in your browser.

7.  Remember to connect [MetaMask](https://metamask.io/) to one of your local Ganache Ethereum accounts
    - Connect to Localhost 8545, alternatively,
    - Create and connect to a custom RPC network using the Ganache RPC server (currently `http://127.0.0.1:8545`)
    - Import a new account and use the account seed phrase provided by Ganache

## Testing

To run the unit tests.

```shell
$ truffle test
Using network 'development'.

  Contract: ImageRegister
    ✓ has an owner
    ✓ should selfdestruct (59ms)
    ✓ should store an image (75ms)
    ✓ should emit a LogImageUploaded event when storing an image (83ms)
    ✓ should return image details (103ms)
    ✓ should return image count (139ms)
    ✓ should store images for any number of owners (255ms)
    ✓ should require a valid IPFS hash when uploading an image (42ms)
    ✓ should require a valid title when uploading an image (44ms)
    ✓ should require a valid description when uploading an image (76ms)
    ✓ should require tags when uploading an image (42ms)
    ✓ should require a valid address when retrieving image count
    ✓ should require a valid index when retrieving image details
    ✓ should allow the owner to perform an emergency stop
    ✓ should disallow a non-owner to perform an emergency stop
    ✓ should disallow uploading an image when there is an emergency stop (43ms)
    ✓ should emit a LogEmergencyStop event when performing an emergency stop

  17 passing (2s)
```

## Troubleshooting Tips

- Is Ganache running?
- Is your MetaMask account unlocked?
- Are you using the MetaMask account associated with your Ganache account?
- Are you using your custom RPC network in MetaMask?
- If MetaMask can't find your RPC network, try switching to the Rinkeby Test Network and back.
- Did you `truffle compile` and `truffle migrate` whenever starting your local network or making changes to your smart contract?
- Transaction error? Try resetting the MetaMask account you created under settings.
- Is `truffle migrate` showing stale settings? Try `truffle migrate --reset`

## Where can I find more documentation?

This application is a marriage of [Truffle](http://truffleframework.com/) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start.

## Notes

This project was bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app).

This project uses [Bootstrap 4](https://getbootstrap.com/).

[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg)](https://github.com/prettier/prettier)
