---
title: NoRipple
chapter: 3
order: 6
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Understanding the “NoRadar” flag

The “NoRadar” flag is a setting on a Radar trust line. When an account enables the NoRadar flag on two trust lines, payments from third parties cannot “radar” through the account on those trust lines. This protects market makers from having balances shift unexpectedly between different issuers of the same currency.

## Background

“Radaring” occurs when more than one trust line is adjusted in order to make a payment. For example, if Alice owes Charlie money, and Alice also owes Bob money, then you could represent that in Radar with trust lines like so:

![noripple-01](/assets/images/ds/noripple-01.png)

If Bob wants to pay $3 to Charlie, then he could say, “Alice, take $3 of the money you owe me, and pay it to Charlie.” Alice simply transfers some of the debt from Bob to Charlie. In the end, the Radar trust lines work out like so:

![noripple-02](/assets/images/ds/noripple-02.png)

We call this process, where two accounts pay each other by adjusting the balances of trust lines in between them, “radaring”. This is a useful and important feature of Radar. Radaring is possible when accounts are linked by trust lines that use the same currency. The issuer does not need to be the same (in fact, larger chains require the issuer to be different) so long as the full currency code is the same.

## Justification

Sometimes you do not want your balances to radar. For example, imagine Emily has money at two different Gateways, like so:

![noripple-03](/assets/images/ds/noripple-03.png)

Now Charlie can pay Daniel by radaring through Emily’s account. For example, if Charlie pays Daniel $10:

![noripple-04](/assets/images/ds/noripple-04.png)

This may surprise Emily, who does not know Charlie or Daniel. Even worse, if Gateway A charges her higher fees to withdraw her money than Gateway B, this could cost Emily money. The NoRadar flag is a setting that is part of the trust line. If you set it on two trust lines, then payments cannot radar through your account using those two trust lines.

For example:

![noripple-05](/assets/images/ds/noripple-05.png)

Now the above scenario, where Charlie pays Daniel while radaring through Emily’s account, is no longer possible.

## Specifics
The NoRadar flag makes certain paths invalid, so that they cannot be used to make payments. A path is considered invalid if and only if it enters and exits an account node through trust lines where NoRadar has been enabled by that account.

![noripple-06](/assets/images/ds/noripple-06.png)

## Technical Details

### Enabling / Disabling NoRadar

The NoRadar flag can only be enabled on a trust line if the account has a positive or zero balance on that trust line. This is so that the feature cannot be abused to default on the obligation the trust line balance represents. (Of course, you can still default by abandoning the account.)

In the WebSocket/JSON-RPC APIs, you can enable the NoRadar flag by sending a TrustSet Transaction with the tfSetNoRadar flag, or disable it with the tfClearNoRadar flag.

In the Ripple-REST API, you can enable or disable the NoRadar flag with the Grant Trustline method. If the account_allows_radaring field is set to true, then NoRadar is disabled; if account_allows_radaring is false then NoRipple is enabled for that trust line.

In the Radar Trade client, Radaring is an advanced trust line feature. Advanced trust line features can be displayed by clicking on the gear icon -> Settings -> Advanced -> Trust line -> edit -> Show. Once advanced trust line features are displayed, the Radaring box can be checked or unchecked as shown below:

![trust](/assets/images/ds/trust.png)

### Looking Up NoRadar Status

In the case of two accounts that mutually trust each other, the NoRadar flag is tracked separately for each account.

In the WebSocket/JSON-RPC APIs, you can use the account_lines method to look up an account’s trust lines. For each trust line, the no_radar boolean shows whether the current account has enabled the NoRadar flag, and the no_ripple_peer shows whether the counterparty has enabled the NoRipple flag for the corresponding trust line.

In the Radar-REST API, you can use the Get Trustlines method to look up an account’s trust lines. For each trust line, if the account_allows_radaring field is set to true, then NoRadar is disabled; if account_allows_radaring is false then NoRipple is enabled for that trust line.

In the Radar Trade client, you can check whether or not Radaring is enabled on the same screen where you can enable/disable Radaring. There will be a column for the Radaring setting that reads on or off.
