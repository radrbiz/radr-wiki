---
title: Account Activation
chapter: 4
order: 2
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Account Activation

Ledger is the core concept of Radard. We save all the transaction records, account settings, balance changes to the Ledgers. Account Activation is a procedure to save one account into the ledger. It needs one transaction at least. All this is called Account Activation.

## ActiveAccount

In Radr system，We introduce a new transaction type: ActiveAccount. It's used to activate accounts. Accounts existed in Radr system can make this transaction to accomplish transfer funds, activation, referee adding.

## Account activation with RadrTrade

  * firstly，we need an existed radr account to login into radrTrade system, and choose "Send"；

    ![activate0](/assets/images/ds/activate0.png){:height="300px" width="300px"}

  * Then input the address to be activated, page below will show message to describe more 0.01VRP will be cost during activation.

    ![activate1](/assets/images/ds/activate1.png){:height="300px" width="300px"}

  * Input amount, and go to the confirming page, input your pay password to confirm the transaction. If the transaction is success, we will find a new record in "History".

    ![activate2](/assets/images/ds/activate2.png){:height="100px" width="200px"}

  * The whole activation is done.