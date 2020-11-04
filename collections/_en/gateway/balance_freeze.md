---
title: Balance Freeze
chapter: 2
order: 4
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Balance Freeze

## Overview

Similar to Bitcoin, Radar implements virtual, physical­like currencies. As with physical coins or paper bills, once a Radar balance is issued, the issuing party relinquishes control of the asset. The users trusting the issuer can pass around the balance person­to­person as they would any other physical coin or note.
This stands in sharp contrast to the “electronic money” managed by traditional financial institutions. In those systems, the institution maintains complete control of all transaction processing. This enables financial institutions the flexibility to stop transaction processing if systems become compromised, or to “freeze” individual account issuances if called upon to do so by authorities.
RadarLab is extending the RTXP to enable support for both physical­like and electronic­like currencies. This will allow gateways additional feature flexibility and in some cases enable compliance with local laws.

## Intended Use of The Freeze Feature

The freeze protocol extension gives gateways the ability to 1) globally freeze all their issued funds, or 2) freeze funds issued to a particular user. Frozen funds may only be sent back to the gateway who issued them.
The global freeze feature allows a gateway to freeze all balances issued by it. The gateway may still issue payments. Accounts holding frozen balances may return the funds to the gateway. This feature is useful for migrating users from one account to another and to safeguard users in the event of a compromise of the gateway account.
The individual freeze is intended primarily for complying with regulatory requirements which may vary from one jurisdiction to another. It also allows gateways to freeze individual accounts issuances in order to investigate suspicious activity. These features allow gateways to better operate in compliance of laws and regulations.

## Opting Out of Individual Account Freeze

Some gateways may want to continue operating under the existing physical­like money system. In these cases, the gateway can permanently disable their own ability to freeze their issued assets individually. By opting out a gateway and its users will continue operating according to the same physical money rules to which they have become accustomed. This prevents gateways from freezing individual account issuances (of the gateway only) in the event that an account is compromised or is engaged in suspicious activity.

## Deciding on a Metaphor

Since the freeze feature represents a significant shift in metaphor, Ripple Labs is encouraging each gateway to decide if they wish to employ or opt­out of these new features. In addition, Ripple encourages each gateway to notify their current users of their decision in advance of the freeze feature taking effect. That will allow users to opt­out and move to an alternate, physical­like money gateway.


To be continued...

(From `GatewayBulletin-BalanceFreeze.pdf`.  @see: 🌐 <https://wiki.ripple.com/Freeze>)

# Related Links
  * [Radar Gateway](../start)