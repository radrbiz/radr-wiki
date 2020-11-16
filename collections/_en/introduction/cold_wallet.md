---
title: RadarWallet Cold Wallet Introduction
chapter: 1
order: 7
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# RadarWallet Cold Wallet Introduction

## Overview

RadarWallet is a cold wallet published by RADR lab, which can protect private keys more safely and assets as well in local environment.

RadarWallet has Windows，OS X，Linux desktop versions. It provides key management, balance checking, transaction signing functions.

![冷钱包](/assets/images/tech/radarwallet.png){:height="400px" width="400px"}

## Safe

Comparing to online wallet, cold wallet is offline. All the functions including account keys are done in local machine, eg: creating new key, storing keys, transaction signing.

The keys stored in cold wallet are encrypted in local. Those operations need security checking require the password of the wallet. Even the user's wallet is hacked by others, the wallet is safe if you keep your password.

RadarWallet has the Import & Export function. Users can dump the private keys into a file, store the file in another safe place, and then import to the cold wallet again when needed. 

This client tool is Open Source. Users can rebuild it by themselves for some reasons.

## Usage

### 1. Create a wallet

When the first time opening RadarWallet, it prompts an box to let you input the password, and then creates a new account address. This password will be used for encrypting keys in wallet. All the operation that need user's key, require the password to verify the accessibility. Remember: use a strong password and keep it in safe. If you lose your password, the assets in the wallet would be lost, too! 

### 2. Manage the addresses

RadarWallet supports multi-address. User can create new address by clicking 'New Address'. By clicking 'Switch Address' to switch current address. And 'Add Private Key' to import an existing address.

All the keys of their addresses are store in encrypted wallet file. Only correct password can touch the assets.

### 3. Transfer

Transfer operation has two main steps: signing and sending. Signing need the user's private key and is done in local. User's private key will never be sent to the network.

Sending the transaction requires the internet and RADR nodes. Cold wallet use default node from RADR lab. Even if the transaction was sent to untrusted node, the asset would not be lost because only signed data was sent.

Due to the feature of BlockChain itself, the transaction would take a few seconds. It takes some time to confirm the consensus from validating nodes. The exact time depends on the network and the current workload. 

### 4. Import & Export

Cold wallet supports Import and Export functions. Use'Import Wallet File' and 'Export Wallet File' to dump out to a safer place or import from existing files. 
