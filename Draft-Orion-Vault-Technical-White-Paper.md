---
title: Orion Vault Technical White Paper
layout: post
author: dawid
permalink: /orion-vault-technical-white-paper/
source-id: 1MzPkFsD6GpjcdF7I0QTOiQP4EPBP0ZdrMsvrc6s-L8I
published: true
---
Orion Vault Technical White Paper (draft)

Version: Draft. Last change: June 4, 2018. Copyright © 2018 Orion Vault

# Abstract

Orion Vault enables an infrastructure for the future of art investments and donations. Provides technological ecosystem and legal framework for creating and tokenizing Digital Masterpieces, facilitating art market economy with Orion Vault Coin, managing assets portfolio and building relationships between users. Assures users' verification & authentication associating an account with an address on Ethereum Blockchain. Brings tools to serialize Digital Masterpieces into fully Digital Asset Class certificates deployable to the blockchain as ERC721 tokens and exchangeable for the Orion Vault Coin ERC20 utility tokens. The art market economy takes place on blockchain being governed by transparent, self-triggering, publicly available Smart Contracts. The top most layer is a platform allowing for account and privacy management, portfolio analysis, Digital Masterpieces exploration and participation in the art market.

# Background

It seems that the art market industry demonstrated unprecedented resistance to major technological breakthroughs. Although internet coverage grows, price of hardware decreases and modern means of creative expression like CG, VR, AR emerge and mature, artists struggle to access investors and monetize their artwork. On the other end investors find the threshold high to enter the market.

Multiple middlemen benefit from each single attempt to perform a transaction. Thus once a deal is made the bottom line musts withstand recurring fees and lengthy procedures. A reserve price, timing and an auction audience composition is driven by middlemen and that all add up to reduced decisions flexibility and further to low artworks velocity on the market.

Beyond the predominant middlemen position on the market there are other natural, interconnected factors that affect investment decisions i.e. low liquidity of assets, their vulnerability to a physical damage, their maintenance costs and provenance assessment risk. Aforementioned lead to a subsequent problem of an art investment aesthetic values precipitation i.e. storing an artwork out of sight for e.g. safety and optimizing tax reasons.

# Objective

To provide a future proof service that enables unconstrained participation in the art market to all internet users. Following requirements have to be met:

* Constitute the independent and transparent digital art assets market by deploying self governing smart contracts to Ethereum Blockchain that describe utility token, Digital Masterpiece and relationships (e.g. patronage and trade),

* Allows for healthy community of verified market participants by requiring one-off identity verification yet giving a choice of remaining anonymous,

* Enable safe interactions on the market by developing an API that securely encapsulate all operations with blockchain with extra security 2FA layer on top,

* Create a framework for issuing Digital Masterpieces to the market by providing a semi-automated, fraud-free process leveraging a legal and art experize, imaging technology and scalable IT solutions,

* Assure discoverability of Digital Masterpieces and market participants by developing an investment tools with social factor accessible on mobile and web.

# Definitions

### Orion Vault - OV

The entire infrastructure of legal framework & IT services.

### Oron Vault Market - OVM

A state of OV-deployed Ethereum Blockchain Smart Contracts and EOAs (Externally Owned Accounts).

### Orion Vault User - OV User

An account of verified user associated with an EOA on blockchain (1:1 relationship).

### Digital Masterpiece - DM

An ERC721 (NOTE:  A standard interface for non-fungible tokens, also known as deeds. (source)) compliant smart contract representing a non-fungible token. A fully digital asset resulting from digitization of OV User's artwork in a format.

### Orion Vault Coin - OVC

An ERC20 (NOTE:  A standard interface for tokens. (source)) compliant utility token serving as a payment medium on the market. 

### Orion Vault Platform - OVP

A suite of client tools (web & mobile) serving as an interface to exercising activities on the market and providing discoverability of OV Users and Digital Masterpieces.

### Orion Vault Website - OVW

An informative internet site (NOTE:  https://orionvault.io) on Orion Vault.

# Blockchain

The Orion Vault Market is core to the entire OV infrastructure. Being built on Ethereum Blockchain leverages an established solution and technology stack embraced by developers worldwide. The OVM is designed as set of relationships between EOAs and Smart Contracts with forward compatibility in mind. A portable architecture would allow major design refactor in future including new art market features and even switching to another blockchain as blockchain technology and paradigm develops over time. In particular Smart Contacts relationship should be upgradeable i.e. designed specifically in a way that overcomes certain Ethereum Blockchain/Solidity limitations.

Execution of Smart Contracts that happens on Ethereum Blockchain is intentionally independent of OV infrastructure. An order on the market is processed by Ethereum network as scheduled by concerned OV Users. An order outcome, either DMs ownership change or OVC balance transfer is publicly visible and the order's execution transparent.

### Orion Vault User Smart Contract

OV User can be seen as a forwarding contract that serves as proxy for EOAs willing exercise activities on the blockchain market. An internet user is granted an account in OV once passed verification. Gets a blockchain EOA associated with it and whitelisted.

### Orion Vault Coin Smart Contract

OVC is an utility token standardized as ERC20. This allows for seamless future adoption i.e. integration with existing wallets and listings on token exchanges. Tokens supply will be known at OVC Smart Contract deploy time and won't change ever.  There are no restrictions on who can own OVC. Orion Vault takes a supervisory role for initial OVC distribution among eligible EOAs either upon pre-sale, ICO or other events.

### Digital Masterpiece Smart Contract

DM is a non-fungible token standardized as ERC721. This allows for seamless adoption i.e. integrated with existing wallets and listings on so called crypto collectibles market. DM supply is an inherent part of an artwork digitization process and can be seen as a last step of the process. It carries certification-like information on issuer, licence and other metadata.

### Orion Vault Market

OVM can be seen as a set of Smart Contracts facilitating relationships between OV Users. There are in particular two relationships: trade and patronage. Both Smart Contracts are so called multisig contracts that execute upon agreement of 2 OV Users i.e. when their EOAs sign a contract. That means these are externally (thus voluntary) triggered contracts. Another class of contracts is Self Triggering Smart Contracts. There are two OVM built in contracts of this kind: Fee Contract and Carry Commision contract. Upon initial agreement of two EOAs the Patronage contract behaves as self triggering smart contract until expiry condition is met.

### Trade Smart Contract

A contract that facilitates an exchange of DM for OVC between two particular users. It triggers upon mutual signatures and causes DM's ownership change along with OVC balance transfer between the transaction parties. The transaction may be liable to other intermediary contracts that are executed independently of external factors and automatically. In particular is always liable to Fee and Carry Commision contract.

### Patronage Smart Contract

A contract that facilitates a long lasting relationship between EOAs. Upon agreement the first EOA commits to transfer agreed OVC balance to the other EOA on regular basis. In return the EOA benefiting from regular OVC transfers commits to transfer shares of OVC every time when managed to trade DMs within contract's validity period.

A particular formula i.e. transfer amount and shares as well as more complex clauses of a contract will be provided as optional and free to choose. Upon OV Users feedback basing on demand new types of patronage formulas can be introduced to the market.

### Fee Smart Contract

A built in contract. The contract deducts an OV Fee from each trade on the blockchain market payable by the site receiving OVC. Although selling DMs for proverbial "$1" is discouraged as negatively affects provenance and eventually asset value provisions in contract state as follows:

* t.b.d.

### Carry Commision Smart Contract

A built in contract. The contract deducts a carry commision from the OV Fee and transfer it to DMs issuer EOA.

### Donation Smart Contract

A special case of a trade contract where a DM is "sold" for zero OVC.

* t.b.d.

# Digitization

OVP, OV User, DM.

# Client applications

OVP, OV User.

# Testing and reliability

Testnet, private blockchain, cloud infrastructure, geographical spread.

# Privacy considerations

OV User.

# Security considerations

Review all.

# Internationalization

OVP, DM.

# Caveats

Upgrading contracts, private keys processing.

# Timeline

Divided in Milestones then Issues (gitHub) among few workstreams.

# Launch

Pilot, Assisted, DMs issuance for selected Museums only, OV Users cap, by invitation only, exclusive.

# Landing

* Pilot ends, all museums can issue a DM, OV Users cap removed, open to selected countries,

* Artists DMs certification, remove country restrictions.

# Conclusion

Interestingly solving the 500 years old debt in the art market industry with technology heals all natural limitations. Seamlessly. Digital Masterpieces being fully digital assets introduce liquidity to the art market and agility to investors. Reduce risk connected to keeping physical goods including costs of regular maintenance, while 3rd party blockchain brings provenance built-in tracking to the entire market for free.

