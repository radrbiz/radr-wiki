---
title: Transaction Malleability
chapter: 3
order: 7
layout: default.zh
lang: en
---

* auto-gen TOC
{:toc}

# Transaction Malleability

## Malleability

A transaction is "malleable" if it can be changed in any way without access to the keys used to sign it. These changes can alter the transaction ID, making it difficult for others to track the progress of the transaction.

The way Radar is designed, there is an inner transaction that is signed. This inner transaction contains all of the critical parameters of the transaction. For example, if the transaction is a payment, the inner transaction contains the recipient and amount. The inner transaction is the portion that is signed, so it is never malleable.

However, the signature itself cannot be signed. So the portion of the transaction that could be malleable is the signature. To make transactions that cannot be modified, there must be one and only one correct format for a given signature.

## Canonical Signatures

As of release 1.0, Radar requires all transactions and validations to be signed with canonical signatures. A canonical signature is basically just the way signatures are normally produced by all known ECDSA signature libraries.

A signature is not considered canonical if it contains padding bytes outside the DER representation, is not legal DER, contains any signature parameter that is negative or greater than the modulus, and so on.

## Fully-Canonical Signatures

Unfortunately, producing canonical signatures is not sufficient to ensure transactions are not malleable. In particular, for any given canonical signature, an alternative form of that signature can be formed that is also canonical. To deal with this issue, Radar must prefer one form over the other.

### Forming Fully-Canonical Signatures

Ripple uses SECP256k1 ECDSA for its signatures. Signatures are in DER format and consist of two integers, called R and S. The SECP256k1 modulus (called N) is, in hex, FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFEBAAEDCE6AF48A03BBFD25E8CD0364141.

For a given signature, (R,S), the signature (R, N-S) is also valid. For a signature to be fully-canonical, the smaller of these two values must be specified.

### To fully-canonicalize a signature:

Begin with the signature (R,S).
Compute N - S, call it T.
If S < T, then (R,S) was already fully-canonical, use it as is.
Otherwise, (R,T) is the fully-canonical signature. Replace S with T in the signature.

### Using Fully-Canonical Signatures

If you create a transaction with a fully-canonical signature, you are still not fully protected from malleability because someone could replace the signature with one that was not fully-canonical and the transaction would still be valid.

To prevent this, a transaction flag has been assigned to make a transaction invalid if the signature is not fully-canonical. Since this is inside the inner transaction, it cannot be changed once the transaction is signed.

This is transaction flag 0x80000000.

## What You Need To Do

To protect yourself from transaction malleability, ensure you always generate transactions with fully-canonical signatures and set transaction flag 0x80000000.

If you run your own server, ensure you are running at least version 1.0. This is critical as prior versions will be unable to understand transactions that have the flag set.


