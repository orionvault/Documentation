---
title: Orion Vault Technical White Paper
layout: post
author: dawid
permalink: /orion-vault-technical-white-paper/
source-id: 1GnUry3Qas4srMEoTEaM5G4dOCfTF19hKIntpcywwImI
published: true
---
Orion Vault Platform Technical White Paper

Version: Draft. Last change: September 28, 2018. Copyright © 2018 Orion Vault AG

# Abstract

Orion Vault Platform (OVP) enables an infrastructure for digital art market providing a technological ecosystem and a legal framework. The art market takes place entirely on Ethereum Blockchain via smart contracts deployed through the platform. OVP ensures identity verification of all market participants whitelisting their Ethereum addresses on the blockchain. To facilitate interactions with the blockchain (either user verification or exercising market activities) OVP offers standalone clients: a mobile app and a DApp. Beyond blockchain interactions they allow for account and privacy management, managing art portfolio and building relationships between galleries, artists and collectors.

# Background

Digital art market is non-digital as there are no means of achieving uniqueness and denoting ownership at internet scale. Artists and galleries consider digital art as traditional turning it physical for market purposes. All lead to non-standardized process of certifying and accounting digital art across galleries. Due to likely mistakes and despite physical nature of digital art market transactions collectors still do not have a future proof guarantee of uniqueness and ownership of a digital art they possess.

It seems the art market demonstrated unprecedented resistance to major technological breakthroughs. Although internet coverage grows, price of hardware decreases and modern means of creative expression like CGI, VR, AR emerge and mature, digital art market remains in the Dark Ages.

# Objective

To enable digital art market to enter the Renaissance 2.0 (NOTE:  https://www.britannica.com/topic/art-market#ref282931) by making it entirely digital. Analogically to the Renaissance era OVP shall bring the best artists, galleries and collectors in one place where they can thrive and benefit from open art market. Where notion of "digital artists" gains more and more currency.

OVP shall provide means of unconstrained participation in the art market to all internet users. Following requirements have to be met:

* To constitute the independent and transparent digital art market by deploying self governing smart contracts to Ethereum Blockchain.

* To allows for healthy community of verified market participants by requiring one-off identity verification yet giving a choice to remain anonymous.

* To allow galleries and curated artists to deploy digital art into the blockchain.

* To equip digital art owners with means of a real time access to the original digital art (a file) in a secure way.

* To assure discoverability of digital art on the market by developing tools available on mobile and web.

# Orion Vault Platform

Technological ecosystem and legal framework enabling an infrastructure for digital art market. Its tech stack consists of:

* Ethereum Blockchain (3rd party) serving as a physical infrastructure for the entire digital art market.

* Smart contracts deployed to the blockchain constituting the digital art market.

* A mobile app that allows for exploration of the digital art market and trading functionalities for verified users.

* A DApp having a functional parity with the mobile app allowing galleries and curated artists to deploy their digital art to the digital market on top of it.

* A back end that facilitates communication between clients (mobile app, DApp) and the blockchain via Infura (3rd party) and support multiple functionalities e.g. users verification, digital art deployment, data pre- and post- processing etc.

* A cloud storage (3rd party) that holds an encrypted digital art available to the owner.

![image alt text](https://raw.githubusercontent.com/orionvault/Documentation/master/public/TFa0jFKOfUa04lXuYdZEpw_img_0.png)

#### Fig. 1 - Orion Vault Platform (gold color) in context of  client (green) and server (red) third party stack.

# Orion Vault Smart Contracts

Smart contracts deployed to the Ethereum Blockchain constituting digital art market. 

### Orion Vault Masterpiece (OVM).

OVM is an ERC-721 standard allowing to represent a single piece of digital art a token in form of a token.

### Orion Vault Masterpiece Escrow (OVME).

An intermediary contract where all the magic happens. One instance is created per each OVM entry (i.e. token) and remains associated with the entry forever. Its only method (a fallback method) is able to receive Ether and responsible for checking for transaction requirements, transferring ownership of the OVM and sharing the ether sent between parties: 90% to a seller as a payment, 5% to an artist/deployer as a carry commission and 5% to Orion Vault as a fee.

### Orion Vault Auction (OVA).

A contract that manage OVM market activities. When an OVM token is set for sale the OVA entry is created. Once OVM token is sold or just taken off from sale the OVA entry is removed.

### Orion Vault Users - (OVU)

OVU are whitelists holding Ethereum addresses. A whitelist denotes a certain role an address is eligible to exercise eg. deploy OVMs or trade OVMs on the market.

#### Fig. 2. - T.B.D.

# Orion Vault Backend

A layer between the blockchain and clients.

# Orion Vault Mobile App

A standalone client available for Android and iOS.

# Orion Vault Mobile DApp

A standalone client available in internet browsers supporting Meta Mask (NOTE:  https://metamask.io/) or similar EVM bridge.

# Use Cases

### Set up an OVP account and login (mobile)

After installing an app on a mobile device a user is ready to explore digital art market. To go beyond "read only" functionalities the user needs to register an account. The simple registration allows to express interest or to “like” a piece of digital art and to create a profile which enables relationships between users.

To be able to participate in the market the user needs to provide an Ethereum account address and identity proof (a combination of passport, utility bill etc.). After successful verification the user is sent a confirmation email. Onwards the user can fully benefit from the platform while still can chose to remain anonymous not to reveal any personal data (e.g. name, country).

#### Fig. 3. - T.B.D.

### Deploy a piece of digital art to the OVP (DApp)

During a registration process a user can apply for special credentials allowing for deployment of digital art pieces to the platform. More thorough process of verification is required to check if the user is an artists or an art institution (e.g. gallery) with capabilities of providing pieces of fine digital art.

An eligible (verified as such) user can deploy an art to the market. The user is required to provide a file of original high quality media, its thumbnail (if the media provided is not image) and various metadata including the piece's title, author’s name etc. After required data is uploaded the user is prompted to sign a transaction via MetaMask in order to deploy OVM token to the blockchain. This act makes the user eligible to benefit from a carry commision from each transaction in which the token is involved.  

#### Fig. 4. - T.B.D.

### Set for sale/set not for sale (mobile & DApp)

Each OVM token in a user's collection can be set for sale. In order to do that the user has to set a price in Ether, create an entry in OVA auction contract,  and approve the OVME escrow contract associated with the token to govern its sale. To make it happen signing a blockchain transaction via MetaMask is required. Similarly to cancel sale and take the OVM token off the auction another MetaMask prompted transaction signature is required. Only owner of the token is eligible to sign transactions.  

#### Fig. 5. - T.B.D.

### Buy (mobile & DApp)

In order to buy an OVM token it is enough to send Ether to its associated OVME contract. Several requirements needs to be met: both seller and buyer are granted credentials to exercise market activities i.e. are verified users, the token associated with OVME remains on sale and Ether amount is exactly as the token's price. 

As all requirements are met the contract cancels auction (removes an entry in OVA contract), transfers ownership of the token to a buyer, cancels itselves approval for govern the token, transfers 90% of Ether amount to seller, 5% to original OVM token deployer (e.g. artist or gallery) and 5% to Orion Vault address as a fee.

The transaction can be initiated either through the DApp via MetaMask or any wallet either mobile, desktop or hardware.

#### Fig. 6. - T.B.D.

### Obtain a file of a digital art piece

During deployment process an original high quality media gets password encrypted and uploaded to cloud. Also the media's hash gets created through a hashing function and becomes a part of its token metadata on the blockchain. The media file is exposed under a permanent, publicly accessible link of format https://_ov_cloud_ /{hash}. Visiting the link starts a file download. Only a user that owns the token and its associated file can decrypt the file using a password available in the user’s OVP account.

Upon token ownership transfer a file under the cloud link associated with the token changes as gets re-encrypted with a password that belongs to the new owner.

#### Fig. 7. - T.B.D.

