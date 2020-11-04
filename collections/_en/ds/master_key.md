---
title: Master Key
chapter: 4
order: 5
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Master Key

## Rationale
In Ripple it is often not trivial to change your account. Other users will have extended trust and IOUs will be owed by a particular account.

Because of this Ripple has a Master/Regular key system. The idea is to allow you to change your often used regular key with your emergency Master key that is stored offline.

## How It Works

The public key of an account serves two purposes. First, the hash of the public key is the account ID. Second, the public key is used to validate the transaction signature. Ripple allows you to use two different keys for each of these purposes.

The account ID is the hash of the master account key. The corresponding private key is needed to create the account. But the account also has a field for a public transaction signing key (called the 'regular account key').

Changing the regular account key is useful if you suspected or knew your account had been compromised. It could also be done routinely, if desired, to protect against the risk of leakage due to keyboard loggers, shoulder surfing, and so on.

## Mechanics

Accounts have two keys:

  * Regular key
     * For every day use.
  * Master key
     * For emergency use only on the most trusted devices.
     * Can be used to change the regular key in the event of possible or actual compromise.
     * Stored or locked away somewhere safe.

## In Practice

To set up an account to using this scheme you do the following steps:

1. Generate your master seed
2. Fund this address from some other account to create it
3. Generate a regular seed
4. Set the Regular seed on your account