---
title: Transaction Privacy
chapter: 3
order: 3
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Transaction Privacy

## Introduction

Transaction privacy protection has always been a very important branch in the history of cryptocurrency development. BIP32, CoinJoin, Zerocoin, Monero and Grin are examples in this direction. In the past, these technologies were mainly applied in UTXO cryptocurrency, such as Bitcoin. How to achieve a better transaction privacy protection of RADR under the World State account model has been a research subject of Radar Lab. Although Ripple and Ethereum share the same model as RADR, they have made slow progress and have no substantial breakthroughs. RADR is the first cryptocurrency that achieves unconditional transaction privacy protection under the World State account model.

The mainstream privacy protection technology consists of CoinJoin, Ring Confidential Transaction, and Zero Knowledge Proof. CoinJoin usually needs a centralized or semi-centralized service. A fully decentralized solution is complex, demanding and rarely achieved, which means unconditional privacy protection is difficult to realize. This option was abandoned after a period of study. We have poured a lot of resources to research Zero Knowledge Proof which was applied in many projects. The results show that this technology also has many disadvantages and two of which have a serious impact on user experience. One is the serious waste of memory space and computational efficiency under the World State account model. This is because  all transaction history of Zero Knowledge Proof has to be saved and used for calculations, and the key fingerprint needs to be saved to prevent double- spending. The other is that a transfer requires four transactions to complete. You need to convert the plaintext balance to a zero-knowledge one and then declare a zero-knowledge balance to be transferred out. The receiver needs to declare a zero-knowledge balance to be transferred in and convert it to plaintext balance. Learn more from [WhitePaper](https://github.com/radrbiz/radard/blob/master/doc/Transaction_Privacy.pdf)。

![tx-privacy](/assets/images/ds/tx-privacy.png){:height="900px" width="900px"}

## Technical Details

We eliminate the correlation between the transaction sender and receiver via a two-step operation of Deposit and Withdraw

1. Deposit
   1. Generate a random key pair (Pk, Sk)
   2. Send the amount and the public key Pk to a ring.
   3. Go to the next step when a certain amount of Pk is accumulated.

2. Withdraw

We let L = {Pk1, ... , Pkn} be an ordered public key set for the ring
   1. Generate ring signature σ and key fingerprint I with the private key Sk and L.
   2. Send ring signature σ and fingerprint I to received amount from the ring.

### Signing algorithm

![sign](/assets/images/ds/sign.png)


## Instructions

### Deposit

#### Conditions of successful deposit
1. Same amount of same asset should be sent to the ring by different addresses. 
2. Wait at least 200 ledgers since the first transaction was sent.
3. 5 txns are needed to make a ring at least, 20 at most.

#### Operation

When initiating a transaction on the private transfer page, the sender should select an amount, and the information of the latest ring will be displayed below.

![deposit](/assets/images/ds/deposit-1.png)

After selected the amount, click next to save the private key information.

>Note: please keep the private key properly to avoid asset loss. Once lost, the asset will be lost forever! 

The format of the private key is like `radr-xx-xx-xxxxxxxxxxxxxx`, We use '-' to divide it into four parts，radr-part1-part2-part3，
1. radr is a reserved field
2. part1: amount of the ring
3. part2: id of the ring
4. part3: private key

![deposit](/assets/images/ds/deposit-1.png)

Finally, click `send VBC` to send the transaction.

### Withdraw

#### Conditions of Withdraw
1. The account to do withdraw cannot be one of the accounts that have make deposit to the ring
2. The withdraw operation can only be performed if the ring is made successful
3. The private key is the only proof of the ownership of the asset, and the loss of the private key means the loss of the asset

#### Operation

The user enters the private transfer `Get` page and enters the private key information.

![withdraw](/assets/images/ds/withdraw.png)


Click `Get VBC` to withdraw. the asset will be sent to the address from the ring. Accordingly, the history of the current withdrawal will be displayed below.

![withdraw](/assets/images/ds/withdraw-1.png)



