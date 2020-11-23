---
title: VBC/WVBC Swap
chapter: 8
order: 2
layout: default.en
lang: en
---

# VBC/WVBC Swap

At present, most of the Ethereum-based DEFI applications are running based on the ERC20 protocol. In order to enable Radar to fully participate in and benefit from the DEFI ecosystem, we have introduced a new Ethereum-based ERC20 token, WVBC (Wrapped VBC), and a swap system that can swap between VBC and WVBC. After being converted into WVBC tokens, users can proform transactions with it in various ERC20-based DEFI applications (such as Uniswap, etc.) on the Ethereum network. This article mainly introduces what WVBC is and how to swap it with VBC.

## What is WVBC

WVBC (Wrapped VBC) is an ERC20 token issued on the Ethereum network that can be exchanged 1:1 with VBC.

Radar Network provides an automatic swap system, which has a publicly auditable Radar account. The account's address is:

```
rsVeqrYjJbYMdar7A6c4EyscZ4WgbY92ys
```

We call this account the **pledge account**. Each WVBC token on Ethereum corresponds to a VBC pledged and frozen in the **pledge account**. The VBC balance of the **pledge account** is publicly auditable and strictly follows conditions as following:

```
Pledge_VBC_Balance ≥ WVBC_Total_Supply
```

To convert VBC to WVBC, go through the following steps:

1. User specifies an Ethereum address to receive ERC20 tokens, and transfers a specified amount of VBC to the **pledge account**
2. The swap system monitors VBC transferred to the ** pledge account**, and transfers  corresponding amount of WVBC to the Ethereum address designated by the user to receive ERC20 tokens through the ERC20 token contract

To convert WVBC to VBC, go through the following steps:

1. The swap system generates a WVBC **withdraw address** for each user (an Ethereum address)
2. User transfers a specified amount of WVBC to his WVBC **withdraw address** through ERC20 transfer operation
3. The swap system monitors the WVBC tokens transferred to the user's **withdraw address**, unfreezes the corresponding amount of VBC from the **pledge account** and transfers it to the user's radar account, and calls the `burn api` of the ERC20 contract to  destroys the corresponding WVBC

The above is the principle and technical implementation of WVBC. In fact, as an end user who does not care about technical details, the actual operation process will be relatively simpler. The next two sections will introduce the swap process of VBC and WVBC from the perspective of a user .

## 2. Convert VBC to WVBC

1. Click `Convert WVBC` under `VBC` section on the `Overview` page (Picture 1)

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v01_convert_wvbc.png)

    Figure 1

2. Choose `convert VBC→WVBC` (Figure 2)
3. Fill in the user's ERC20 token deposit Ethereum address (Figure 2)
4. Fill in the amount of `VBC` to be exchanged (in Figure 2)
5. Click "Confirm" (Figure 2)
6. The exchange history can be viewed on the `Convert WVBC Record` blockchain (Figure 2)

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v02_to_wvbc.png)
    
    Figure 2

Precautions:

1. The swap process will charge a fee on the Ethereum network, and the fee will calculated as VBC and charged on the radar network. WVBC received by the user is the amount after fee charging.
2. In order to reduce fee wasted by small exchange, the swap system requires the minimum swap amount to be 10 VBC
3. The conversion process needs to wait for the radar transaction confirmation first, and then wait for the Ethereum transaction confirmation, so it needs to wait for confirmations to complete

## 3. Convert WVBC to VBC

1. Click `Convert WVBC` under the `VBC` section of the `Overview` page (Figure 1)
2. Choose `Convert WVBC→VBC` (Figure 3)

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v03_to_vbc.png)
    
    image 3

3. Copy `WVBC` **Redeem address** (Figure 3)
4. Fill the copied **return address** into the transfer destination address of the ERC20 wallet, and transfer the specified amount of `WVBC` tokens to this address
5. After the exchange is completed, the exchange history can be viewed in the conversion `WVBC` record block (Figure 3)

Precautions:

1. The swap process will generate a handling fee on the Ethereum network. The handling fee (gas) for WVBC transfer is collected by the user's ERC20 wallet, and the remaining handling fee (such as WVBC burning gas) will be converted into WVBC and collected by the exchange system. The user actually receives The VBC is the amount after deducting the handling fee

2. The minimum exchange amount required by the exchange system is 1 VBC. WVBC transfers less than 1 will be ignored and will not be refunded

3. The redeemed WVBC transfer operation is carried out in the user’s ERC20 wallet, and the radar network does not participate in the process, so the user must ensure that the entered **return address** is correct. Entering the wrong address will cause the WVBC token to be lost and cannot be found Back to

4. The conversion process needs to wait for the transaction confirmation of the Ethereum network first, and then wait for the transaction confirmation of the radar network, so it will take a while to complete
