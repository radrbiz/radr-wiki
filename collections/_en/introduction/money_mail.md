---
title: MoneyMail
chapter: 1
order: 5
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# MoneyMail

1. Transfer money to a mailbox from Transfer page；

    ![money-mail](/assets/images/money_mail/moneymail-en-1024x388.png){:height="300px" width="300px"}

2. Transfer money to a mailbox by sending email
3. There are four types of recipients:
    * mailbox not registered yet
    * mailbox registered but not activated yet
    * mailbox registered and activated，but address not activated on the chain.
    * mailbox registered and activated，address activated on the chain.

The last 2 types will be processed as normal transfer, and the first 2 types will trigger `MoneyMail Transfer`.

## Transfer money to a mailbox from Transfer page

### Rules

1. MoneyMail uses official currency list as: `CNY,BTC,ETH,VBC,VRP,XRP,EOS,BCH`
2. For non 'VRP' tranfer, The first account who makes the tranfer need to add an additional `0.01VRP` as the transaction fee for the recipient.
3. The system will deduct the asset and `fee` after MoneyMail transfer has been made: the fee calculation rules is listed [below](# MoneyMail fee calculation).
4. The period of the transfer's validity is 7 days, asset will be refunded if expired（Tips: VRP fee won't be refunded.)；
5. The system will send a mail containing a link to the recipient's mailbox after the asset and fee deduction has done.
6. The recipient need to click the link in the email to receive the asset.
7. After the recipient's registration, the system will send the asset to his account automaticly.
8. Recipient can login to view the progress of the transfer.

##  Transfer money by sending email

### Rules

1. First of all, the account needs to enable this function on the setting page and set the upper limit of CNY amount (Note: different currencies are converted into CNY value according to real-time price) within 24h, as shown in the following image:

    ![money-mail-settings](/assets/images/money_mail/settings-money-mail-en.png){:height="200px" width="150px"}

2. MoneyMail uses official currency list as: `CNY,BTC,ETH,VBC,VRP,XRP,EOS,BCH`
3. The email format requirements: 
    * Title：Number of amount + space + currency, for example: `200 CNY`
    * CC `mm@radarlab.org` is required.
4. For non 'VRP' tranfer, The first account who makes the tranfer needs to add an additional `0.01VRP` as the transaction fee for the recipient.
5. The system will deduct the asset and `fee` after MoneyMail transfer has been made: the fee calculation rules is listed [below](# MoneyMail fee calculation).
6. The period of the transfer's validity is 7 days, asset will be refunded if expired（Tips: VRP fee won't be refunded.)；
7. The system will send a mail containing a link to the recipient's mailbox after the asset and fee deduction has done.
8. The recipient need to click the link in the email to receive the asset.
9. After the recipient's registration, the system will send the asset to his account automaticly.
10. Recipient can login to view the progress of the transfer.

## MoneyMail History

View the MoneyMail History by category selection on the tranfer page: [🌐 https://t.radarlab.org/transfer](https://t.radarlab.org/transfer)

![money-mail-cn](/assets/images/money_mail/transfer-cat-en.png){:height="150px" width="150px"}

## MoneyMail fee calculation

A fixed `0.011VRP` will be charged for every MoneyMail transfer.

### Fee for first transfer

* For VRP, no need to have the attatched fee of `0.01VRP`

    ```
    fee=Math.max((amount+0.011)/1000, 0.001) + 0.011(MoneyMail) VRP
    ```

* VBC (along with `0.01VRP`)

    ```
    fee = Math.max(amount/1000, 0.001) + 0.01(Attatched fee) + 0.011(MoneyMail) + 0.001(transaction fee for 0.01VRP) = 0.022 + Math.max(amount/1000, 0.001) VRP
    ```

* Other currencies (along with `0.01VRP`)

    ```
    fee = 0.001(transaction fee) + 0.01(Attatched fee) + 0.011(ActiveAccount) + 0.001(transaction fee for 0.01VRP)) = 0.023 VRP
    ```

### Fee for non first transfer

* VRP, no need to have the attatched fee of `0.01VRP`

    ```
    fee = Math.max((amount+0.011)/1000, 0.001) + 0.011(MoneyMail) VRP
    ```

* VBC

    ```
    fee= Math.max(amount/1000, 0.001) + 0.011(MoneyMail) + 0.001(transaction fee for VRP) VRP
    ```

* Other currencies

    ```
    fee=0.001(Transaction fee) + 0.011(MoneyMail) + 0.001(transaction fee for VRP) = 0.013 VRP
    ```
