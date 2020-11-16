---
title: Account
chapter: 4
order: 1
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Account

## Overview

A RADAR Account is an entry in the Ledger. People typically have one account that stores their RADAR credits, IOUs and the trust paths granted to and from other accounts. Each account has an address and a private key. Anyone that knows an account's private key can authorize transactions from that account.

A RADAR account:
  * has an address similar to rHb9CJAWyB4rj91VRWn96DkukG4bwdtyTh(starts with 'r'); OR nickname like ~nickname(begin with '~').
    *  [Encodings](../encodings)
    * Addresses have built in checksums. It is extremely unlikely for a typo to be considered a valid address.
  * holds a balance of VRP/VBC
  * may hold IOUs issued by other accounts
  * may extend trust to other accounts（Commonly is a [Gateway](../../gateway/start)）
  * may place offers currency exchange

Account balances, trust limits, and payments are public information. No one will know who each account is associated with except to the extent that they can uncover such information based on the account's transactions, behavior, correlations with other accounts and entities via databases, etc.

Each RADAR account has an address which others can use to:
  * send funds to the account
  * extend trust to the account

## How to create a new account

You can use command line, RPC/Websocket API...

For command line examples: 

```
radar@s1-1:/opt/radar$ ./radard wallet_propose any-your-other-passphrase-donot-use-this
{
   "result" : {
      "account_id" : "rHapkyzZ58aVxEADpYK6czCSzQ831jN4Gu",
      "master_key" : "MOLT FOLK LYLE DEED JAG EGG ROW CORK BUSS HAL DAR DEL",
      "master_seed" : "ssnohWqEzs5Hehz5KuKHDkrUhmqmT",
      "master_seed_hex" : "1BD6508C8569CD3821F4C138D482F0BD",
      "public_key" : "aBMzBCw7cssQ3KurJ5KneVaURXZxRZ31E6WwvN2qbWn5vScXZDMW",
      "public_key_hex" : "0203D2B88CB9ED006929EF19D2C5F7ECCC29C11FDF0F272F5A68C6B057400375B8",
      "status" : "success"
   }
}
```

## master_seed 

In RADAR and any other crypto-currency, the essence of an account is a 'public/private' key pair. The account_id is calculated by public key, public key depends on private key, and the private key could be generated from a seed（a shorter string, starts with 's'）.

The decision chain is：

master_seed ----> private key ----> public key ----> address(account_id)

------

## Validating Addresses

An address can be validated with the RPC account_info. This function can determine if the address is legal and if it currently exists in the ledger.

In radar-lib, use UInt160.is_valid(x) to validate an address.

A Radar address may be verified with Bitcoin address code, if the Bitcoin alphabet/dictionary is replaced the the Radar one:

The base58 dictionary for radar is: rpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCg65jkm8oFqi1tuvAxyz
This code may work: 🌐 <https://github.com/shtylman/bitcoin-address/blob/master/base58.js>

## Special Accounts

### ACCOUNT_ZERO

rrrrrrrrrrrrrrrrrrrrrhoLvTp

### ACCOUNT_ONE

rrrrrrrrrrrrrrrrrrrrBZbvji

### The root account

rHb9CJAWyB4rj91VRWn96DkukG4bwdtyTh

## ACCOUNT_ZERO

ACCOUNT_ZERO has the address rrrrrrrrrrrrrrrrrrrrrhoLvTp, also known as ADDRESS_ZERO, and is used as VRP's issuer. Additionally, in paths this account specifies that a path node refers to an order book. In decimal, this account has an address of 0.

## ACCOUNT_ONE

ACCOUNT_ONE has the address rrrrrrrrrrrrrrrrrrrrBZbvji, also known as ADDRESS_ONE, and is used as a neutral account, most significantly in Ripple state entries. In decimal, this account has an address of 1.

## The root account

Account rHb9CJAWyB4rj91VRWn96DkukG4bwdtyTh is the root account. This account starts with all the VRP when the genesis ledger is created. This address is derived from the secret pass phrase "masterpassphrase" and is often used as a generic account in examples.

Deriving the seed and account id for the root account:

```
# radard -q wallet_propose masterpassphrase
{
   "result" : {
      "account_id" : "rHb9CJAWyB4rj91VRWn96DkukG4bwdtyTh",
      "master_seed" : "snoPBrXtMeMyMHUVTgbuqAfg1SUTb",
      "master_seed_hex" : "DEDCE9CE67B451D852FD4E846FCDE31C",
      "status" : "success"
   }
}
```

## Black Hole Addresses
Addresses for which no one has the private key are effectively black holes: VRP sent to those address are effectively lost forever.

Typically, these addresses will be easily recognizable as being astronomically hard to have been generated with a corresponding private key. For example, these address will often begin with many 'r's.
  * rrrrrrrrrrrrrrrrrrrrBZbvji - ACCOUNT_ONE
  * rrrrrrrrrrrrrrrrrrrn5RM1rHd - NaN as per radar-lib.
  * rrrrrrrrrrrrrrrrrNAMEtxvNvQ - Used for Radar name reservation fee.
An alternative way of destroying VRP is to simply spend it as a transaction fee. The AccountSet transaction can be used as a no-op transaction for just destroying VRP.

# Other Language
  * [Chinese](/zh/ds/account)

# Related Links

  * [Radar System](/en/)
  * [Radar Gateway](../../gateway/start)
  * [Encodings](../encodings)
  * [Master Key](../master_key)


