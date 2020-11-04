---
title: 第三方平台接入说明
chapter: 1
order: 6
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 第三方平台接入说明

## 说明

### 发行

为了确保用户在第三方平台上进行交易时可以获得发行收益，第三方平台上的用户必须设置一个在`radard`链上激活的地址。参见 [创建帐户](https://radarlab.org/dev/transactions.html#creating-accounts)，查看 [获取帐户信息](https://www.radarlab.org/dev-cn/radard-apis.html＃account-info) 以获取更多信息。

第三方平台每天都会将这些数据与 `radarlab.org` 同步。

为此，第三方平台必须实现：

  * 第三方平台必须申请API密钥；
  * 第三方平台为 `VBC` 生成一个地址作为其 `热钱包`。参见[🌐 如何创建账号](https://radarlab.org/dev/transactions.html#creating-accounts)
  * 让用户为每个用户设置一个地址或生成一个关联的地址。
  * 每天使用sync API同步数据。
  * 获得收益。
    * 如果用户设置了自己的地址，请登录 🌐  <https://t.radarlab.org>以查看余额。
    * 如果为用户生成了地址，则第三方平台会将资产分配给用户。

## 充提

### 存款

第三方平台会扫描其存款地址的 `transactions`。
  * RPC-API [account_tx](https://radarlab.org/dev/radard-apis.html#account-tx)
  * `DestinationTag`：任意标签，用于标识向目的地付款或向其付款的托管钱包的原因，在这里可以用来标识不同的用户。参见[🌐 Payment/DestinationTag] (https://radarlab.org/dev/transactions.html#payment)

### 提款

第三方平台需要自己签名，然后广播到 `radard`。
  * 如何签署`tx`：[sign-tx](https://radarlab.org/dev/radard-apis.html#sign)
  * Java代码参考：[sign-tx-with-java](https://github.com/radrbiz/radarj/blob/master/radar-lib/src/test/java/org/radarlab/test/TestTxn.java)

## 资源列表

### 基础文档

  * `radarj`: 🌐  <https://github.com/radrbiz/radarj>
  * `radard` doc: 🌐  <https://radarlab.org/dev/radard-apis.html>
  * `radard` transactions doc: 🌐 <https://radarlab.org/dev/transactions.html>
  * `radar RPC tools`: 🌐 <https://info.radarlab.org>
  *  get the chain ledgers info: 🌐 <https://www.radarlab.org/dev-cn/radard-apis.html#ledger-closed>
  * `radard` endpoints:
    * websocket: wss://s1.radarlab.org:5006, wss://s1.radarlab.org:443, wss://s2.radarlab.org:5006, wss://s2.radarlab.org:443 
    * https: https://s3.radarlab.org:443, https://s3.radarlab.org:5005

###  API 

#### 同步API 

  * 用于在第三方平台和 `radarlab.org` 之间同步数据的API 
  * url: https://t.radarlab.org/api/open/syncAccount
  * 参数

|Name | Desc |
|-- | -- |
|hotwallet | 第三方平台热钱包地址|
|data | json格式账号数据, 例如: {"address1": "122.12","address2": "12.1"}|
|sign | md5(data+signKey), signKey 由 `radarlab.org` 下发|
|pubKey | `hotwallet`公钥|
|secretSign | keyPair.sign(data)|

  * 结果
  
```
//Rsponse
{"status":"success"}
```

#### 可靠交易检查

阅读 [可靠交易](https://radarlab.org/dev/reliable_tx.html) 以获取更多信息.

`radarlab.org`现在提供了一个API，以检查`tx`是否成功。

  * url: https://t.radarlab.org/api/open/search/{txnHash}

  * 参数
	* txnHash string
  * 返回

```
//Tx failed
{
	"data": {
		"error_code": "TXN_NOT_FOUND",
		"message": "Transaction not found"
	},
	"status": "failed"
}

//tx under confirmation
{
	"data": {
		"error_code": "TXN_STATUS_UNKNOWN",
		"message": "Transaction is being confirmed"
	},
	"status": "failed"
}

//tx success
{
	"date":1590378811000, //timestamp
	"Account":"rhkWqtdPifimovdzTyoFpxRFNNkUfq5Sis",  //sending account
	"Destination":"rppwViZj28MwZH17Rf261EMDLiwUVsLYVT", //recipient 
	"TransactionType":"Payment",  //Transaction type
	"ledger_index":31133277,  //leder number where tx is
	"SigningPubKey":"036c05124ac31194de381eb89356326295bf3a1de80c188c764569a05281109acf",
	"Amount":{ //Amount object
		"currency":"ETH",  //currency
		"value":"17.695", //value,
		"issuer":"rag51TScTzzMLFc5ZYDSA6mEfH3AM4kvCz" //gateway address
	},
	"Fee":"1000", //fee
	"Flags":2147483648,
	"Sequence":15334,  
	"LastLedgerSequence":31133280,
	"TxnSignature":"304402207a38b91a4c74ee975f7341e514190aaab11d3a6b1ac8130756311590ce3371f002200cfd6aed28b7f81027c05f616a2f06fee8b10448b132171320fd4df7d389fc40",
	"validated":true,
	"DestinationTag":158523,  //DestinationTag
	"hash":"3D9E48BBBB6CF8E067F14C227326E306B55737FF04874CE4A2828C64496D0CBD". .//tx hash
}
```

### Jave 代码


#### 如何创建账号

```
Wallet wallet = new Wallet();
String address = wallet.account().address;
String seed = wallet.seed();
```

#### 如何获取公钥和签名

```
String seed = "snoPBrXt...fg1SUTb"; // seed of address
String data = "testdatadata"; // data to be signed
KeyPair keyPair = (KeyPair) Seed.getKeyPair(seed);
String secretSign = new String(Hex.encode(keyPair.sign(data.getBytes()))); //signed data
String pubKey = keyPair.pubHex(); // public key
```

### 如何接入

请第三方平台发送邮件到 <dev@radarlab.org> 申请接入相关事宜。
