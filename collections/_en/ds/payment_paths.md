---
title: Payment Paths
chapter: 4
order: 6
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Payment Paths

## Overview

A payment path indicates a path through which currencies can flow. A payment path consists of one or more links. Each link specifies an account to ripple through or to use an offer from. A link may optionally specify the output currency and issuer.

Payment paths are specified in a context:

  * The sending account.
  * The receiving account.
  * The send amount.
    * This is the amount, currency, and issuer to deliver to the receiver.
  * The maximum send amount.
    * This is the amount, currency, and issuer to at most deduct from the sender.
    * If not specified it defaults to the send amount.

## Usage

For VRP to VRP transactions, there is no need to construct path nor estimating and setting a maximum cost.

For transactions involving credit paths, payment paths are constructed as part of the transaction. Except for very short paths, constructing a path is likely beyond the resources of thin clients. Clients may ask servers to construct a path for them. Servers are not required to provide a path or provide the best path. Typically, a client which does not have access to a trusted server would ask multiple untrusted servers for a path and then use the path with the lowest rate.

For transactions possibly involving transfer fees, quality fees, and offers a maximum cost must be specified to prevent the user from being surprised at the actual cost of the transaction. This is because the network state is constantly changing. At the time the transaction is actually processed, the liquidity may have changed for better or worse.

A transaction actually takes a set of paths. A path set may only have one source currency. When the transaction is completed, the liquidity described by the path set is taken in order from least to most expensive liquidity. This gives the payer the best available rate for the path set provided.

Typically:
  - someone accepting a payment states: the amount, the currency desired, the Ripple address, and a transaction id to the payer.
  - The payer enters this information into their wallet.
  - The wallet requests a path and cost from servers.
  - The wallet displays a maximum send amount computed by adding a fixed percentage to the cost. The user approves the transactions.
  - The wallet signs and sends the transaction to the Ripple network.

## Representation

The first link of a payment path is implied:
  * the sender's account.
  * the currency is taken from the maximum send amount.
  * for non-VRP the issuer is the sender's account.

The last link of a payment path is implied:
  * the receiver's account.
  * the currency is taken from the send amount.
  * for non-VRP the issuer is the receiver's account.

If needed, the second link is implied from the send max.

If needed, the second to last link is implied from the send amount.

Offer links can immediately follow each other, if they share a currency and issuer.

Adjacent links which do not differ by currency imply an offer link between them.

Adjacent links which have an output issuer which is not the is of the link accounts, imply a link composed of the issuer as account and issuer.

Payment links are applied in order until the destination amount is satisfied.

Expanded format:
  * Only used notionally.
  * All implied links are instantiated.

Compressed format:
  * Canonical format for paths.
  * Required for use in transactions.
  * No optional information that may be implied is allowed.
    * No links that may be implied are allowed.

Notes:
  * VRP may not be rippled.
  * VRP may only be at the ends and in between offers.

## Binary format

See: Binary format

## English explanation

If you think about a payment path, the sender is obviously always the first link in the path and the recipient is always the last link.

For a source currency other than VRP, if the second link in the path is an account, then that path will result in the sender spending funds only on their ripple line to that second link. So if I make a payment spending BTC with Bitstamp's account as the link after me, then I'll wind up holding less BTC/Bitstamp as a result of the payment.

For a destination currency other than VRP, if the second to last link in the path is an account, then that path will result in the recipient receiving funds only on their ripple line to that account. So if someone makes a payment paying me BTC and puts Bitstamp's account as the link before my account, then I'll wind up holding more BTC/Bitstamp as a result of the payment.

To avoid having to use paths all the time, Ripple permits you to specify an account as the SendMax issuer. That implicitly puts that account before every specified path. Similarly, Ripple permits you to specify an account as the Amount issuer. That implicitly puts that account after every specified path. The default paths are affected as well.

So, for example, if Bitstamp wants to send me 1 BTC, but issue the transaction from their hot wallet, they can sign the transaction from their hot wallet account but specify their issuer account as the SendMax issuer. Now they don't need a path.

Of course, most of the time you don't want to limit the transaction. Typically, the sender is willing to use any funds they have for that currency and will pay the recipient from any account they'll accept. To specify this, you use the account that's already there. The sender is already first in every path, so you specify the sender as the issuer of the SendMax amount to have no effect. The recipient is already last in every path, so you specify the recipient as the issuer of the destination Amount to have no effect.

Default paths are only useful for same currency transactions. Cross-currency transactions always need at least one order book and currently, no order books are used in default paths. (Perhaps in the future, order books to and from VRP or order books directly from the source to destination currencies will be considered default paths, so they'll work cross currency, but not yet.) The default path is always: sender -> SendMax issuer (if not sender) -> Amount issuer (if not recipient) -> Recipient

Non-default paths are: sender -> SendMax issuer (if not sender) -> path as specified in the transaction ->Amount issuer (if not recipient) -> Recipient

## API

See: ripple_path_find
