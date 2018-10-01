---
title: Orion Vault Technical White Paper
layout: post
author: dawid
permalink: /orion-vault-technical-white-paper/
source-id: 1GnUry3Qas4srMEoTEaM5G4dOCfTF19hKIntpcywwImI
published: true
---
Orion Vault Platform Technical White Paper

Version: Draft. Last change: September 30, 2018. Copyright © 2018 Orion Vault AG

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

### Orion Vault Masterpiece (OVM)

OVM is an ERC-721 standard allowing to represent a single piece of digital art a token in form of a token.

### Orion Vault Masterpiece Escrow (OVME)

An intermediary contract where all the magic happens. One instance is created per each OVM entry (i.e. token) and remains associated with the entry forever. Its only method (a fallback method) is able to receive Ether and responsible for checking for transaction requirements, transferring ownership of the OVM and sharing the ether sent between parties: 90% to a seller as a payment, 5% to an artist/deployer as a carry commission and 5% to Orion Vault as a fee.

### Orion Vault Auction (OVA)

A contract that manage OVM market activities. When an OVM token is set for sale the OVA entry is created. Once OVM token is sold or just taken off from sale the OVA entry is removed.

### Orion Vault Users - (OVU)

OVU are whitelists holding Ethereum addresses. A whitelist denotes a certain role an address is eligible to exercise eg. deploy OVMs or trade OVMs on the market.

![image alt text](https://raw.githubusercontent.com/orionvault/Documentation/master/public/TFa0jFKOfUa04lXuYdZEpw_img_1.png)

#### Fig. 2 - Relationships mapping  between Orion Vault smart contract entries (tokens). OVUsers contract (gold color) is governed by OV and contains accounts of verified users.  Other contracts  (yellow) are independent of Orion Vault and trigger either upon user signing a transaction or trigger as a result of another contract's call.

# Orion Vault Backend

Orion Vault Backend is responsible for bridging communication between the blockchain, OV Mobile App, OV DApp  and the users. It is built with scalability and security in mind utilizing well-known production ready technologies.

Python is used as a main programming language, taking advantage of Django framework to build stable services.  API is created for communication with web services providing all functionalities. Backend API is deployed in Google Cloud Platform to provide quick scaling capabilities along with MSSQL database hosted in Microsoft Azure which allows database for auto-clustering.

Different technologies are being used to contribute to backend performance and maintenance like Redis for cache mechanisms and Celery framework for asynchronous tasks.

![image alt text](https://raw.githubusercontent.com/orionvault/Documentation/master/public/TFa0jFKOfUa04lXuYdZEpw_img_2.png)

#### Fig. 3 - Architecture of Orion Vault Backend public interface specific code (green color) all dependent on  Orion Vault core code (yellow) with internal functions (gold). External services (red).

### Main tasks & flow

When deployed for the first time, API reads blockchain information and transforms it into more user-friendly database format. Such approach allows end user to quickly sort, filter and search required data. There is software in place which constantly check for blockchain changes to correctly reflect actual blockchain state in mobile applications.

Beyond blockchain interactions, OV Backend serves as a communication channel with end users via emails. Confirmation messages are send to notify customers regarding important events being account registration, art purchase and such.

API also acts as a service provider for data storage of platform media assets. Application handles assets with extra security in mind and adopts Google Cloud Storage.

### REST API Documentation

http://test-platform-api.orionvault.com/docs/

# Orion Vault Mobile App

A standalone client available for Android and iOS. The mobile app is built in Visual Studio 2017 using the Xamarin Forms tools. This approach allow us to code the business logic once in C#,  and to share that code between Android and iOS, while at the same time using native components and libraries from both platforms.

![image alt text](https://raw.githubusercontent.com/orionvault/Documentation/master/public/TFa0jFKOfUa04lXuYdZEpw_img_3.png)

#### Fig. 4 - Architecture of Orion Vault Mobile App with Android and iOS specific code (green color) both dependent on  Orion Vault developed code (yellow)  with access to Service Layer (gold). Build on Xamarin Forms with C#.

### Xamarin Forms + C#

The underlying tools and programming language the app is build on.

### Service layer

* Authentication Service allowing for authentication leveraging third party accounts such as Google and Facebook. Additionally it provides Microsoft Azure authentication, and a dedicated authentication server within Orion Vault Backend.

* OV Server Service providing access to Orion Vault Backend for authentication, profiles, art, and artist management.

* Local Database Service used as a cache of local data when the mobile device is not connected to the internet.

* Caching Service manages the access to the server data and cache data.

### Shared Code

Programmed in C#, it represents the core of the application, contain the business logic, access to services and the application's UI

### Android and iOS App

Contains platform specific code for Android and iOS

# Orion Vault DApp

A standalone client available in an internet browsers that supports Meta Mask (NOTE:  https://metamask.io/) or similar EVM bridge. A DApp (Distributed Application) is simply a website with capability of accessing Ethereum Node via EVM bridge. The Orion Vault DApp uses MetaMask browser extension/addon to accomplish that thus using Chrome or Firefox is recommended (which is industry standard).

MetaMask should also hold OV user's registered Ethereum address which means holding the address and its private key allowing the owner to sign blockchain transactions. 

Having access to Ethereum Blockchain the DApp can call methods of Orion Vault Contracts previously deployed to the blockchain. Any read only blockchain routines result instantly without any interaction needed. All read/write routines i.e. those which write to blockchain prompt user through a MetaMask pops up where signature and gas payment is required.

Between the website and MetaMask the DApp contains smart contracts ABI (Application Binary Interface) which is generated during blockchain smart contracts compilation. The ABI serves as a JS manifest file that is leveraged by a third party library (truffle-contract.js) to proxy MetaMask communication. 

The Website itself is built with Angular framework and TypeScript using Material Design libraries for UI.

#### ![image alt text](https://raw.githubusercontent.com/orionvault/Documentation/master/public/TFa0jFKOfUa04lXuYdZEpw_img_4.png)Fig. 5 - Orion Vault DApp constituted by a website and a smart contracts ABI with use of third party JS libs (yellow, light green) in context of its execution environment (green): MetaMask speaking to OV Smart Contracts on the blockchain and a browser communicating with Orion Vault Backend.

# Use Cases

### Set up an OVP account and login (mobile)

After installing an app on a mobile device a user is ready to explore digital art market. To go beyond "read only" functionalities the user needs to register an account. The simple registration allows to express interest or to “like” a piece of digital art and to create a profile which enables relationships between users.

To be able to participate in the market the user needs to provide an Ethereum account address and identity proof (a combination of passport, utility bill etc.). After successful verification the user is sent a confirmation email. Onwards the user can fully benefit from the platform while still can chose to remain anonymous not to reveal any personal data (e.g. name, country).

### Deploy a piece of digital art to the OVP (DApp)

During a registration process a user can apply for special credentials allowing for deployment of digital art pieces to the platform. More thorough process of verification is required to check if the user is an artists or an art institution (e.g. gallery) with capabilities of providing pieces of fine digital art.

An eligible (verified as such) user can deploy an art to the market. The user is required to provide a file of original high quality media, its thumbnail (if the media provided is not image) and various metadata including the piece's title, author’s name etc. After required data is uploaded the user is prompted to sign a transaction via MetaMask in order to deploy OVM token to the blockchain. This act makes the user eligible to benefit from a carry commision from each transaction in which the token is involved.

### Set for sale/set not for sale (mobile & DApp)

Each OVM token in a user's collection can be set for sale. In order to do that the user has to set a price in Ether, create an entry in OVA auction contract,  and approve the OVME escrow contract associated with the token to govern its sale. To make it happen signing a blockchain transaction via MetaMask is required. Similarly to cancel sale and take the OVM token off the auction another MetaMask prompted transaction signature is required. Only owner of the token is eligible to sign transactions.  

### Buy (mobile & DApp)

In order to buy an OVM token it is enough to send Ether to its associated OVME contract. Several requirements needs to be met: both seller and buyer are granted credentials to exercise market activities i.e. are verified users, the token associated with OVME remains on sale and Ether amount is exactly as the token's price. 

As all requirements are met the contract cancels auction (removes an entry in OVA contract), transfers ownership of the token to a buyer, cancels itselves approval for govern the token, transfers 90% of Ether amount to seller, 5% to original OVM token deployer (e.g. artist or gallery) and 5% to Orion Vault address as a fee.

The transaction can be initiated either through the DApp via MetaMask or any wallet either mobile, desktop or hardware.

### Obtain a file of a digital art piece (mobile & DApp)

During deployment process an original high quality media gets password encrypted and uploaded to cloud. Also the media's hash gets created through a hashing function and becomes a part of its token metadata on the blockchain. The media file is exposed under a permanent, publicly accessible link of format https://_ov_cloud_ /{hash}. Visiting the link starts a file download. Only a user that owns the token and its associated file can decrypt the file using a password available in the user’s OVP account.

Upon token ownership transfer a file under the cloud link associated with the token changes as gets re-encrypted with a password that belongs to the new owner.

