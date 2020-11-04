---
title: RADR Wiki
layout: default.en
lang: en
permalink: /en/
---

* auto-gen TOC
{:toc}

# RADR System

RADR([🌐https://radarlab.org/en/](https://radarlab.org/en/)) is a ripple-protocol-based (RTXP) financial network to promote and develop the fastest and least expensive payment settlements system and exchange system on a global scale. It enables payments in all types of currency as easy as sending email. 

RADR is similar to Bitcoin in that it enables users across the network to make p2p transaction but with the benefit that it is currency neutral for real-time clearing and settlement through a series of currency issuers called gateways. This greatly reduces the time needed for transaction clearing including the costs of bank wire transfer.

As the core component of the radar network, the underlying Radard is a series of servers that run peer to peer software. Anyone can freely set up a Radard server to being accepting or receiving payments. In addition to VRP, Radar network introduces a second native currency 'VBC' which is designed to promote the spread and adoption of the Radar network through a reward program. The reward program will be scheduled daily to distribute the pre-defined currency fairly to every eligible user. Using Radard is free and the Radar network is owned by every participant.

For more details about RADR, see [General Introduction to RADR](./introduction/introduction).

## OpenSource
  * Server Code: 🌐 <https://github.com/radrbiz/radard>
  * Java Client: 🌐 <https://github.com/radrbiz/radarj>
  * Cold Wallet: 🌐 <https://github.com/radrbiz/radar-wallet>

## Projects & Products

  * RADRInfo: [🌐 Public information](https://info.radarlab.org/#/ledger) (Realtime data like Ledger,Tx,Account...) of Radar.
  * RADRTrade: [🌐 Radar Trade System (Official trader website)](https://t.radarlab.org/index.html) , [Help Document](./introduction/trade_help)]
  * RADRCharts: [🌐 RADR Charts of trading](https://charts.radarlab.org/)
  * RADR APP: [🌐  iOS & Android APP download](https://www.radarlab.org/en/download.shtml), 
  * Development Docs: 🌐 <https://radarlab.org/dev/>

## Technical Details

| | Document |
| --- | --- | 
| Data Structure: | [Account](./ds/account) , [Transit_Fees](./ds/transit_fees) |
| API Flags: | Understanding [NoRipple](./tech/noripple) flag |
| Knowledge Center: |[Knowledge Center](./introduction/knowledge_center)|

## Key Roles

  * [Gateway Introduction](./gateway/start)
  * [Market Maker](/marketmaker/start)

## Other features

### Public Ledger As Trading Mechanism
The public ledger on RADR network is jointly managed by all the decentralized servers in a process that takes a few seconds. Unlike traditional centralized payment methods, decentralized servers on RADR network uses a consensus algorithms to validate changes on the ledger. The validation will only take place when majority of validator nodes agree that that signature on the payment is correct. In order to change the general ledger data, during every Ledger period, trusted nodes called Validators do work to confirm the digital signatures of transactions are valid, and if found to be valid update their local copy of the database, so any time that all users share ledger of ledger wide consistency. If Consensus is not reached, the Validator nodes wait on processing a transaction until it is a provably true event, otherwise the transaction is rejected.

Consensus algorithm provides users convenient, safe and reliable real-time settlement services. It greatly differentiates RADR from Bitcoin. Unlike Bitcoin which needs dedicated computer “miners” to verify transactions, consumption of energy resources is completely unnecessary on RADR network. 

RADR uses a public ledger to ensure every transaction within the network is transparent and is not under the complete control of any single organization or institution.

### Math Based Cryptocurrency

A special property of RADR is the ability to issue digital assets which can be verified with cryptographic signatures. When backed by a service provider that promises to redeem these assets (gateway), they can hold value such as fiat currencies. These assets can then be traded on the peer to peer network for any type of asset issued by a gateway.

The RADR protocol issues two native currencies VRP and VBC that are created on the genesis ledger. The supply of these currencies is strictly limited in the software that controls the RADR protocol and the issuance cannot be changed or modified after the network is launched.

## License 
RADR is open source and permissively licensed under the ISC license. See the LICENSE file for more details.

## Transaction Fees
[Transaction Fee](./introduction/transaction_fee)

## Contact us

| Name | Emails |
| --- | --- | 
|Customer Service | <radar@radarlab.org> |
|Developer Help | <dev@radarlab.org> |
|Want to start a gateway? | <dev@radarlab.org> |

# Other Language
  - [Wiki in Chinese](/zh)






