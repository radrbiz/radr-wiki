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

$$VRATE=USERi/\Sigma_{i=1}^nUSERi$$

The rank of account's VBC balance is the weight of this part.

## 2. Dividend by spread

The power of account's spread, is defined as all of its invitees' holdings (balances).

![div2](/assets/images/tech/div2.png)

In the following picture,

* "T"(accumulated holdings) == "AMTj" in formula above.
* "T" is called "TSPRD" also in somewhere.
* "B" means balance of The account.

![div-en](/assets/images/tech/div-en.png)

***Related Links***

* [Radar Wiki Homepage](/en/)
* [The fee of transaction](/../../introduction/transaction_fee)
* [Dividend in Chinese Version](/zh/tech/dividend)
