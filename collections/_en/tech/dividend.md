---
title: Dividend
chapter: 3
order: 1
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# The Algorithm of Daily Dividend

* System pays dividends in a fixed time every day. Since 2018-1-7, ratio has been adjusted to 0.10% .
* The volume of each account's dividends is defined by the following algorithm.

## 1. Dividend by holdings

$ VRATE=USERi/\\\sum_{i=1}^nUSERi $

The rank of account's VBC balance is the weight of this part.

## 2. Dividend by spread

The power of account's spread, is defined as all of its invitees' holdings (balances).

$ VRATE=SPDSi/\\\sum_{i=1}^nSPDSi $

$ SPDSi=\\\sqrt[3]{MAX(AMTj)} + \\\sum_{j=1}^m(AMTj < 10000 ? AMTj * 10 : (AMTj - 10000 + (10000 * 10))) $

In the following picture,

* "T"(accumulated holdings) == "AMTj" in formula above.
* "T" is called "TSPRD" also in somewhere.
* "B" means balance of The account.

![div-en](/assets/images/tech/div-en.png)

***Related Links***

* [Radar Wiki Homepage](/en/)
* [The fee of transaction](/../../introduction/transaction_fee)
* [Dividend in Chinese Version](/zh/tech/dividend)
