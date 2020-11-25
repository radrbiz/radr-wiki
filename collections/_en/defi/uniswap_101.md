---
title: Uniswap 101
chapter: 8
order: 1
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Uniswap 101

Uniswap is currently one of the hottest DEFI projects. It is a decentralized token exchange protocol running on Ethereum, which can provide liquidity services for ETH and ERC-20 tokens.

WVBC is an ERC20 token issued on the Ethereum network that can be exchanged 1:1 with VBC. For the introduction and method of obtaining WVBC, please refer to the document ["VBC/WVBC Swap"](../VBC_WVBC).

This article mainly introduces how to use and trade WVBC in Uniswap.

## ERC20 wallet

To use WVBC and other ERC20 transactions on Uniswap, first you need to have an ERC20 wallet. We recommend you to use MetaMask. This article will take MetaMask as an example to explain in detail.

### 1. Install and MetaMask

1. First, you need to install Chrome, Microsoft Edge, or Firefox. Here we take Chrome as an example.
2. Install the MetaMask plug-in, open the URL [https://metamask.io/download.html](https://metamask.io/download.html), and install it according to the instructions on the page

    ![](/assets/images/defi/uni101/a01_metamask_download.png)

Or directly open the Chrome store [Metamask plug-in page](https://chrome.google.com/webstore/detail/nkbihfbeogaeaoehlefnkodbefgpgknn) to install.

   ![](/assets/images/defi/uni101/a02_metamask_chrome.png)

### 2. Initialize MetaMask

1. To use the MetaMask plug-in for the first time, it needs to be initialized, click on `Get Started`

    ![](/assets/images/defi/uni101/a03_metamask_get_started.png)

2. If you already have a seed phrase, you can initialize it by importing a seed phrase. Assuming you don't have phrase, click `Create a Wallet`

    ![](/assets/images/defi/uni101/a04_metamask_create_a_wallet.png)

3. On the `Help Us Improve MetaMask` page, click on `No Thanks` or `I Agree`, depending on whether you want to share non-sensitive data with MetaMask to improve user experience

    ![](/assets/images/defi/uni101/a05_metamask_agreement.png)

4. The `Create Password` page requires you to specify the password of the wallet, at least 8 characters, this password will be used when operating the wallet, please ensure the strength of the password and keep it properly

    ![](/assets/images/defi/uni101/a06_metamask_new_password.png)

5. `Secret Backup Phrase` Here you will be prompted to keep the seed secret key phrase. Click `CLICK HERE TO REVEAL SECRET WORDS` in a secure environment to display the secret key. Use a secure method (for example, you can write it on paper and put it in In your safe) record these phrases. **Note that this is the only basis for restoring your wallet account. People who have these phrases can restore your wallet and manipulate the assets in these phrases**

    ![](/assets/images/defi/uni101/a07_metamask_backup_phrase.png)

    ![](/assets/images/defi/uni101/a08_metamask_backup_phrase1.png)

6. On the `Confirm your Secret Backup Phrase` page, click the words in the order recorded in the previous step to confirm your seed phrase

    ![](/assets/images/defi/uni101/a09_metamask_confirm_phrase1.png)

7. Click `All Done` on the `Congratulations` page, and your wallet will be created

    ![](/assets/images/defi/uni101/a10_metamask_all_done.png)

### 3. Get  WVBC (optional)

If you want to sell VBC through Uniswap, you need to convert your VBC to VBC's ERC20 token WVBC. For the conversion method, please refer to the article ["VBC/WVBC Swap"](../VBC_WVBC).

If there is no WVBC under your `Assets` list, you need to add it to the assets list:

1. Click `Add Token`

    ![](/assets/images/defi/uni101/a12_metamask_add_token.png)

2. Select `Custom Token`
3. Fill in the WVBC token address `0x9c088f5b2c4d364447e111d55504eb564f54d184` in `Token Contract Address`, MetaMask will automatically fill in other fields, please make sure the information you see is consistent with the following picture

4. Click `Next`

    ![](/assets/images/defi/uni101/a14_metamask_custom_token_wvbc.png)

5. Click `Add Tokens` to add WVBC to the asset list

    ![](/assets/images/defi/uni101/a15_metamask_custom_token_wvbc1.png)

6. The WVBC entry will now be displayed in your asset list

    ![](/assets/images/defi/uni101/a18_metamask_token_list.png)

### 4. Get ERC20 tokens (optional)

If you want to buy VBC through Uniswap or want to add liquidity into the Uniswap pool to obtain profit, you need to send corresponding ERC20 token (such as USDT) to your wallet.

The method is similar to the method of ETH or WVBC, just act in the method you are familiar with.

### 5. Get a small amount of ETH

Uniswap is a DEFI application based on Ethereum. Any transaction in Uniswap requires a small amount of ETH to be used as a fee (gas), so we need to get a small amount of ETH into the MetaMask wallet to conduct Uniswap transactions.

1. First, find the ETH address of your wallet, click on your account name on the MetaMask page, the page will automatically copy your ETH address to the clipboard

    ![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

2. You can transfer ETH to your MetaMask wallet in various ways:
     1. Direct transfer from your other ETH wallet
     2. If you have an ETH balance in Radar Wallet, you can choose to withdraw coins to your MetaMask wallet address
     3. If you trade all ETH balances in other exchanges, you can withdraw ETH to your MetaMask wallet address in the exchange
3. Withdrawal or transfer operations need to wait for the Ethereum network to confirm the transaction, so it will take a while to see your ETH balance in the wallet.

## Connect wallet and Uniswap

You can open the Uniwap trading page through the URL [https://app.uniswap.org/](https://app.uniswap.org/). Before performing any type of operation, you need to connect Uniswap to your wallet.

1. Click the `Connect to a wallet` button

    ![](/assets/images/defi/uni101/a19_uniswap_connect_to_wallet.png)

2. Select `MetaMask` in the pop-up list

    ![](/assets/images/defi/uni101/a20_uniswap_wallet_list.png)

3. MetaMask plug-in will pop up a dialog box, click `Next`

    ![](/assets/images/defi/uni101/a21_uniswap_metamask.png)

4. Click `Connect`

    ![](/assets/images/defi/uni101/a22_uniswap_metamask1.png)

5. Wait for a while, you can connect successfully

    ![](/assets/images/defi/uni101/a23_uniswap_metamask_doing.png)

    ![](/assets/images/defi/uni101/a24_uniswap_metamask_done.png)

## Swap WVBC

Uniswap supports swapping between any Uniswap ERC20 token pairs. This section explains the basic operation steps for users who are not familiar with Uniswap to swap WVBC.

1. Select the `Swap` tab in Uniswap
2. Select the token pair to be swaped. If there is no WVBC, you can fill in the WVBC contract address `0x9c088f5b2c4d364447e111d55504eb564f54d184` in the search box to find it. After searching for WVBC, click Add to add it to the common list. Next time WVBC will Directly in the list

    ![](/assets/images/defi/uni101/a26_uniswap_add_wvbc.png)

3. In the same way, add the corresponding token (such as USDT) to the list
4. Choose the token pair to be exchanged, and choose the exchange direction (such as USDT→WVBC or WVBC→USDT, etc.), fill in the amount of exchange, just fill in one of them, and the amount of the other party will be calculated based on the current price.

    ![](/assets/images/defi/uni101/a30_uniswap_do_swap.png)

5. If you are using a token on uniswap for the first time, you will see the following page, requiring advanced authorization operations. If not, skip to step 8

    ![](/assets/images/defi/uni101/a27_uniswap_swap.png)

6. Click `Approve WVBC` to authorize, and the MetaMask plugin will be invoked to sign and authorize and send the transaction

    ![](/assets/images/defi/uni101/a29_uniswap_approve_waiting.png)

7. Wait for `Approve` transaction confirmation
8. After confirming the price and quantity, click the `Swap` button, and click `Confirm Swap` on the confirmation page. The MetaMask plugin will be invoked to authorize the signature and send the transaction

    ![](/assets/images/defi/uni101/a31_uniswap_confirm_swap.png)

    ![](/assets/images/defi/uni101/a32_uniswap_sign_swap.png)

    ![](/assets/images/defi/uni101/a33_uniswap_send_swap.png)

9. After the transaction is confirmed, you can check the swaped token balance in the MetaMask wallet

## Add liquidity

Uniswap supports liquidity mining, and users can add liquidity into Uniswap to gaining profit.

Since profits are in the form of tokens, and the price of tokens fluctuates, users should fully understand Uniswap's liquidity mining mechanism to avoid unnecessary losses.

1. Select the `Pool` tab and select `Add Liquidity`

    ![](/assets/images/defi/uni101/a34_uniswap_pool.png)

2. Select the token pair to increase liquidity (such as WVBC/USDT). If the corresponding token is not found, first add it by referring to step 2 in the previous chapter
3. Fill in the amount to be exchanged, just fill in one of them, and the other will be automatically calculated according to the ratio of the fund pool

    ![](/assets/images/defi/uni101/a35_uniswap_add_liquidity.png)

4. If the token is not approved, please refer to steps 5-7 in the previous chapter for authorization
5. Click `Supply`, click `Confirm Supply` on the confirmation page, the MetaMask plug-in will be invoked to authorize the signature and send the transaction

    ![](/assets/images/defi/uni101/a36_uniswap_add_liquidity1.png)

    ![](/assets/images/defi/uni101/a37_uniswap_add_liquidity2.png)

6. After the transaction is confirmed, you can see the list of participating liquidity pools on the `Pool` page, where you can view your overview of the liquidity pool

    ![](/assets/images/defi/uni101/a41_uniswap_pool_list.png)

7. If the above list is not displayed, you can import it manually
   * Click on `Import it` on the page below
   
    ![](/assets/images/defi/uni101/a39_uniswap_pool_import.png)
    
   * Select the token pair, and click `Manage this pool` to add the token pair pool to the list
   
    ![](/assets/images/defi/uni101/a40_uniswap_pool_usdt_wvbc.png)

## Remove liquidity

If users want to withdraw from liquidity mining and get back the added funds, they need to perform liquidity removal operations. The removal of liquidity will refund the user's pledged tokens according to the current price. It should be noted that due to the principle of Uniswap, changes in the proportion of funds in the mining pool will cause changes in prices, and the amount of tokens actually refunded to users may not be the same as the amount originally added by users.

1. Select the `Pool` tab, and find the token pair to remove liquidity under the `Your liquidity` list. If not, refer to step 7 of the previous chapter to add

    ![](/assets/images/defi/uni101/a41_uniswap_pool_list.png)

2. Click the `Remove` button and select the ratio to be removed on the `Remove Liquidity` page. This page will roughly calculate the amount of the two tokens that can be redeemed after removal

    ![](/assets/images/defi/uni101/a42_uniswap_pool_remove.png)

3. Click `Approve`, MetaMask plug-in will be invoked to authorize the signature and send the transaction

    ![](/assets/images/defi/uni101/a43_uniswap_pool_remove_sign.png)

4. Waiting for the transaction confirmation, the liquidity removal operation is completed, and the redeemed token balance can be checked in the MetaMask wallet

## Disclaimer

1. When VBC is converted to WVBC, it will enter the Ethereum network to circulate. The Radar network will not and have no ability to intervene in WVBC circulating on the Ethereum network. Users need to fully understand the operating mechanism of the Ethereum network to use WVBC.
2. Uniswap is a public DEFI project running on Ethereum. Radar does not participate in the development, operation and maintenance of Uniswap. All Uniswap operations involving WVBC by users are considered to be carried out with a full understanding of the principles and risks of Uniswap, and any gains and losses arising therefrom have nothing to do with Radar.
3. The MetaMask wallet mentioned in this article has no interest relationship with Radar. Users need to fully understand its principles and use risks. Radar is not responsible for any problems arising from using the wallet.
