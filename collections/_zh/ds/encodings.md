---
title: 编码Encodings
chapter: 4
order: 2
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 编码Encodings

所有编码都是为了便于人的阅读。

|Name|编码|版本号|细节描述|负载字节|编码后最大长度|
|--|--|--|--|--|--|
|validation_public_key	|nXXXXX	|28	|Validation public key for node.	|33 bytes	|53|
|validation_private_key	|pXXXXX	|32	|Validation private key for node.	|32 bytes	|52|
|account_id	|rXXXX	|0	|Short name for sending funds to an account.	|20 bytes	|35|
|account_public_key	|aXXXX	|35	|Account public key.	|33 bytes	|53|
|account_private_key	|pXXXX	|34	|Account private key.	|32 bytes	|52|
|family_public_generator	|fXXXX	|41	|Family public generator. <br> Used to generate public accounts.	|33 bytes	|53|
|family_seed <br> validation_seed	|sXXXX	|33	|Family seed. The private generator used to generate public generator and private keys. Random or the first 128 bits of the SHA512 hash of the passphrase.	|16 bytes	|29|

## 注意

* RADAR使用的 base58 字典表: rpshnaf39wBUDNEGHJKLM4PQRST7VWXYZ2bcdeCg65jkm8oFqi1tuvAxyz

  * RADAR地址可以用比特币地址算法验证，只需要替换下比特币地址的字典表。
  * 也可以用js实现: 🌐  <https://github.com/shtylman/bitcoin-address/blob/master/base58.js>

* 编码算法是用base58算法计算： version + payload + 4 byte checksum

  * 4字节的校验码能够减少拼写等错误率到 2^32分之一

* 校验码是对 version and payload 做 sha256/sha256哈希计算，再取前4字节
* Versions是为了编码后首字母固定, 以及编码后的字符串长度稳定.

  * 🌐 [List of address prefixes](https://en.bitcoin.it/wiki/List_of_address_prefixes)
  * 不幸的是，对于32字节的负载，只有2个前缀是稳定的， 其中一个用来给account_id。

## 地址图标

* 🌐 <http://en.wikipedia.org/wiki/Identicon>

  * Clients should show a visible icon to help users identify mistypes addresses.

* 🌐 <https://github.com/thevash/vash>

  * We should probably use this - Need a free licensed JavaScript version.

## 相关链接

* 🌐 [Some evidence on multi-word passphrases](http://www.lightbluetouchpaper.org/2012/03/07/some-evidence-on-multi-word-passphrases/)
* 🌐 [RFC1751: A Convention for Human-Readable 128-bit Keys](http://tools.ietf.org/html/rfc1751)
* 🌐 <http://passfault.com>
* 🌐 <http://www.1337pages.com/password/>
* 🌐 <http://passwordgrid.com>
* 🌐 <http://www.vvsss.com/grid/>
* 🌐 <http://solstice.dhiver.pagesperso-orange.fr/password-grids.html>

***其他语言***

* [英语](/en/ds/encodings)
