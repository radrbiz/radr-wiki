---
title: Encodings
chapter: 4
order: 3
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Encodings

All encodings are for human use.

|Name|Encoding|Version|Description|Payload|Maximum Characters|
|--|--|--|--|--|--|
|validation_public_key	|nXXXXX	|28	|Validation public key for node.	|33 bytes	|53|
|validation_private_key	|pXXXXX	|32	|Validation private key for node.	|32 bytes	|52|
|account_id	|rXXXX	|0	|Short name for sending funds to an account.	|20 bytes	|35|
|account_public_key	|aXXXX	|35	|Account public key.	|33 bytes	|53|
|account_private_key	|pXXXX	|34	|Account private key.	|32 bytes	|52|
|family_public_generator	|fXXXX	|41	|Family public generator. <br> Used to generate public accounts.	|33 bytes	|53|
|family_seed <br> validation_seed	|sXXXX	|33	|Family seed. The private generator used to generate public generator and private keys. Random or the first 128 bits of the SHA512 hash of the passphrase.	|16 bytes	|29|

## Notes:

  * The base58 dictionary for RADAR is: rpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCg65jkm8oFqi1tuvAxyz
    * A RADAR address may be verified with Bitcoin address code, if the Bitcoin alphabet/dictionary is replaced the the RADAR one.
    * This code may work: 🌐  <https://github.com/shtylman/bitcoin-address/blob/master/base58.js>
  * Encodings are base58 of version + payload + 4 byte checksum.
      * The 4 byte checksum makes the odds of accidental construction of a valid encoding 1 in 2^32, if using the same alphabet.
  * Checksums are the first 4 bytes of the sha256 of sha256 of the version and payload
  * Versions are chosen for first character stability, minimum length short address, and output length stability.
    * 🌐  [List of address prefixes](https://en.bitcoin.it/wiki/List_of_address_prefixes)
    * Unfortunately only 2 prefixes are stable for 32 byte payloads and one of these prefixes is used for account IDs. This forces private keys to have the same prefix.

## Address icons:
  * 🌐  <http://en.wikipedia.org/wiki/Identicon>
    * Clients should show a visible icon to help users identify mistypes addresses.
  * 🌐  <https://github.com/thevash/vash>
    * We should probably use this - Need a free licensed JavaScript version.

## 相关链接:
  * [Binary_Format](../binary_format)
  * 🌐  [Some evidence on multi-word passphrases](http://www.lightbluetouchpaper.org/2012/03/07/some-evidence-on-multi-word-passphrases/)
  * 🌐  [RFC1751: A Convention for Human-Readable 128-bit Keys](http://tools.ietf.org/html/rfc1751)
  * 🌐  <http://passfault.com>
  * 🌐  <http://www.1337pages.com/password/>
  * 🌐  <http://passwordgrid.com>
  * 🌐  <http://www.vvsss.com/grid/>
  * 🌐  <http://solstice.dhiver.pagesperso-orange.fr/password-grids.html>

# Other Language
  * [Chinese](/zh/ds/encodings)
