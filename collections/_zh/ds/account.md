---
title: 账号（Account）
chapter: 4
order: 1
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 账号（Account）

## 概览

账号是RADAR总账里的一个实体。通常人们拥有一个账号，保存着他们的RADAR借贷记录，期票（IOU），信任路径和对其他账号的信任关系。任何人知道一个账号的私钥，就能够授权这个账号发起交易（也就是拥有私钥就拥有该账号的一切）

一个RADAR账号:
  * 有一个地址像这种形式：rHb9CJAWyB4rj91VRWn96DkukG4bwdtyTh('r'打头); 或者一个昵称像：~nickname('~'打头).
    * [编码](../encodings)
    * 地址内含校验码。确保不太可能发生打字错误。
  * 持有 VRP/VBC 余额
  * 可能持有另一个账号发出的 期票（IOU）
  * 可以设置对另一个账号（通常是[网关Gateway](../../gateway/start)）的信任（该账号就可以给你发行货币期票）
  * 可以挂单，进行货币兑换

账号余额，信托额度，支付 都是公开信息。没人能够知道账号对应谁。

每一个RADAR账号都有一个地址，用于别的账号可以：
  * 发送自己到该账号
  * 扩大信托额度到该账号

## 创建一个新账号

可以使用命令行, RPC/Websocket API 等方式。

用命令行方式举例：

```
radar@s1-1:/opt/radar$ ./radard wallet_propose any-your-other-passphrase-donot-use-this
Loading: "/home/radar/.config/radar/radard.cfg"
Connecting to 0.0.0.0:5005
{
   "result" : {
      "account_id" : "rHapkyzZ58aVxEADpYK6czCSzQ831jN4Gu",
      "master_key" : "MOLT FOLK LYLE DEED JAG EGG ROW CORK BUSS HAL DAR DEL",
      "master_seed" : "ssnohWqEzs5Hehz5KuKHDkrUhmqmT",
      "master_seed_hex" : "1BD6508C8569CD3821F4C138D482F0BD",
      "public_key" : "aBMzBCw7cssQ3KurJ5KneVaURXZxRZ31E6WwvN2qbWn5vScXZDMW",
      "public_key_hex" : "0203D2B88CB9ED006929EF19D2C5F7ECCC29C11FDF0F272F5A68C6B057400375B8",
      "status" : "success"
   }
}
```

### master_seed

**种子秘钥** (Master Seed)：

在RADAR系统和其他任何的加密货币系统里，账号的本质，都是一个“公钥/私钥”密钥对。account_id(账号地址)是从公钥计算出来的，公钥可以从私钥计算出，私钥可以从一个seed（更简洁的字符串，‘s’打头）计算出。

账号的多个属性，决定链条如下：

```
master_seed ---> private key ---> public key ---> address(account_id)
```

❗️所以说，对于一个RADR里的账户，最重要、最私密的，是“种子秘钥”，这个秘钥字符串一定要保存好，不能泄露导致被外人看见和记录。


