---
title: MetaMask 101
chapter: 8
order: 4
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# MetaMask 101

MetaMask is a simple and easy-to-use ETH wallet. It runs as a browser plug-in on the desktop, and as an APP on mobile phones. This article uses the desktop browser plugin as an example to introduce the basic installation and usage of MetaMask.

## 1. Install MetaMask

1. First, you need to install Chrome, Microsoft Edge, or Firefox. Here we take the Chrome as an example.

2. Install the MetaMask plug-in, open the URL [https://metamask.io/download.html](https://metamask.io/download.html), and install it according to the instructions on the page

     ![](/assets/images/defi/uni101/a01_metamask_download.png)

Or directly open the Chrome store [Metamask plug-in page](https://chrome.google.com/webstore/detail/nkbihfbeogaeaoehlefnkodbefgpgknn) to install

   	![](/assets/images/defi/uni101/a02_metamask_chrome.png)

## 2. Initialize MetaMask

1. To use the MetaMask plug-in for the first time, it needs to be initialized, click on `Get Started`

    ![](/assets/images/defi/uni101/a03_metamask_get_started.png)

2. If you already have a seed phrase, you can initialize it by importing the seed phrase. If you don’t have a seed phrase, click `Create a Wallet`

    ![](/assets/images/defi/uni101/a04_metamask_create_a_wallet.png)

3. On the `Help Us Improve MetaMask` page, either click on `No Thanks` or `I Agree`, depending on whether you want to share non-sensitive data with MetaMask to improve user experience or not

    ![](/assets/images/defi/uni101/a05_metamask_agreement.png)

4. The `Create Password` page requires you to specify the password of the wallet, at least 8 characters, this password will be used when operating the wallet, please ensure the strength of the password and keep it safe

    ![](/assets/images/defi/uni101/a06_metamask_new_password.png)

5. `Secret Backup Phrase` Here you will be prompted to keep the seed secret key phrase. Click `CLICK HERE TO REVEAL SECRET WORDS` in a secure environment to display the secret key. Use a secure method (for example, you can write it on paper and put it in In your safe) record these phrases. **Note that this is the only basis for restoring your wallet account. People who have these phrases can use these phrases to restore your wallet and manipulate the assets in it**

    ![](/assets/images/defi/uni101/a07_metamask_backup_phrase.png)

    ![](/assets/images/defi/uni101/a08_metamask_backup_phrase1.png)

6. On the `Confirm your Secret Backup Phrase` page, click the words in the order recorded in the previous step to confirm your secret key phrase

    ![](/assets/images/defi/uni101/a09_metamask_confirm_phrase1.png)

7. Click `All Done` on the `Congratulations` page, and your wallet will be created

    ![](/assets/images/defi/uni101/a10_metamask_all_done.png)


## 3. Deposit a small amount of ETH

Any DEFI application based on Ethereum needs to consume a small amount of ETH fee(gas), when sending any transaction, so we need to deposit a small amount of ETH into the MetaMask wallet to act any transaction through MetaMask.

1. First, find the ETH address of your wallet, click on your account name on the MetaMask page, the page will automatically copy your ETH address to the clipboard

     ![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

2. You can transfer ETH to your MetaMask wallet in various ways:
      1. Direct transfer from your other ETH wallet
      2. If you have an ETH balance in Radar Wallet, you can choose to withdraw coins to your MetaMask wallet address
      3. If you trade all the ETH balance in other exchanges, you can withdraw ETH on the exchange to your MetaMask wallet address
3. Withdrawal and transfer operations need to wait for the Ethereum network to confirm the transaction, so it takes a while to see your ETH balance in the wallet.


## 4. Deposit ERC20 tokens

[ERC20](https://eips.ethereum.org/EIPS/eip-20) is a universal token interface standard in the Ethereum network. It is a very common operation to receive or send tokens through the ERC20 protocol.

### Add tokens to wallet

If the token you want to send or receive does not appear in your asset list, you need to add it manually.
1. Click `Add Token`

     ![](/assets/images/defi/uni101/a12_metamask_add_token.png)

2. If the token to be added is a common token, select `Search`, enter the name of the token, click the token to be selected from the list, click `Next`, and then click `Add Tokens` Add coins to the asset list
3. If the token you want to add is not a common token, select `Custom Token`, fill in the contract address of the token in `Token Contract Address`, MetaMask will automatically fill in other fields, and the information you see is similar to the picture below

![](/assets/images/defi/uni101/a14_metamask_custom_token_wvbc.png)

Click `Next`, click `Add Tokens` to add tokens to the asset list

![](/assets/images/defi/uni101/a15_metamask_custom_token_wvbc1.png)

### Receive tokens

Receiving tokens is very simple. Just send your ETH address to the person who sent the tokens. Find the ETH address of your wallet and click on your account name on the MetaMask page. The page will automatically copy your ETH address to the clipboard

![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

Send this address to the person who sent the token by any means, and the other party can send the token to you.

### Send tokens

1. Select the token to be sent in the token list
2. Click `Send`
3. Enter the recipient's ETH address in the input box
4. In `Amount`, fill in the amount sent
5. Click `Next`
6. Click `Confirm`
