---
title: Transaction Fees
chapter: 1
order: 4
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Transaction Fees

  - Activating the wallet（Creating an account）：Require a transfer to the newly created account from an existing account, whose owner needs to pay 0.01 VRP plus transaction fee for the transfer（see Point 2 for details).
  - Transaction fee for a transfer
    - A transfer of VBC or VRP: the sender needs to pay a bill 1/1000 of the transfer amount in terms of VRP as the transaction fee, and the minimum of such a transaction fee is 0.001VRP.
    - Transfer of other currencies: a fixed transaction fee, which is 0.001 VRP
    - Other types of transaction, e.g. Offer: a fixed transaction fee, which is 0.001 VRP
  - Reserves are not needed. There is no minimum balance required for a wallet,  i.e. the total balance can be transfer into an activated account.
  - Note: If VRP balance equals to ZERO, the account could not issue any more transactions, unless other accounts transfer some VRP (more than 0.001) to it. 

------

## Fee Terminology

Terminology should be consistent. The terms are as follows:

### Reference Transaction

A basic account to account transfer of VRPs.

### Base Fee (fee_base)

The cost, in VRP, of the reference transaction assuming no load on the network. This is the knob that gets turned to adjust transaction fees based on the scarcity of VRPs.

### Fee Units

A measure of the relative cost of different things such as transactions, reserves, and so on. If one transaction costs twice as many fee units as another, it will cost twice as much to process under the same conditions. The conversion of fee units to VRP needed to perform a transaction depends on the base fee, the reference fee, and load.

### Reference Fee (fee_ref)

The cost, in fee units, of the reference transaction.

### Reserve Base (reserve_base)

The amount needed to create an account, in fee units.

### Reserve Increment (reserve_inc)

The amount of additional reserve required for each counted owner entry, in fee units.

### Load Base (load_base)

The value of the load fee that indicates that there is no additional fee imposed due to load.

### Local Load Fee

The multiplicative adjustment to fees based on load on a particular server. A value equal to the load base indicates only normal fees apply.

### Network Load Fee

The multiplicative adjustment to fees based on load to the network as a whole.

### Load Fee (load_fee)

The greater of the local load fee and the network load fee. This is the actual factor used by a server when deciding whether a transaction has an adequate fee.

### Load Factor (load_factor)

The amount a fee has to be multiplied by to convert from the fee required under no load to the transaction fee required under current load.

# Other Language

  * [Chinese](/zh/introduction/transaction_fee)

# Links
  * [Transit Fees](../../ds/transit_fees)
