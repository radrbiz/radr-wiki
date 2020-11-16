---
title: Third-party Issuance Interface Instructions
chapter: 1
order: 6
layout: default.en
lang: en
---

* auto-gen TOC
{:toc}

# Third-party Issuance Interface Instructions

## Description

### Dividend

RADR released a set of third-party issuance interfaces, supporting issuance income calculations of the third-party institutions and exchanges. 

For obtaining the dividend while trading on third-party platforms, users on third-party platforms must set an address which was activated at `radard` main network. See [🌐 creating-accounts](https://radarlab.org/dev/transactions.html#creating-accounts), [🌐 get-account-info](https://www.radarlab.org/dev-cn/radard-apis.html#account-info) for more information.

Third-party platforms SHOULD synchronize these data with `radarlab.org` every day.

For third-party issuance, outer platforms MUST implement:

  * Third-party platforms apply for an API key;
  * Third-party platforms generate an address as their `hotwallet` for `VBC`. see [🌐 how-to-create-address](https://radarlab.org/dev/transactions.html#creating-accounts)
  * Let user set an address or generated an associated address for every user.
  * Synchronize data using the sync API every day.
  * get the profit.
    * if user set his own address, login 🌐  <https://t.radarlab.org> to view the balance.
    * Third-party platforms distribute the asset to the user if generated address for the user.

## Deposit and Withdraw 

### Deposit

Third-party platforms scan the `transaction` of it's deposit address. 
  * RPC-API [account_tx](https://radarlab.org/dev/radard-apis.html#account-tx)
  * `DestinationTag`: Arbitrary tag that identifies the reason for the payment to the destination, or the hosted wallet to make a payment to, which is used to identify different users. see [🌐 Payment/DestinationTag] (https://radarlab.org/dev/transactions.html#payment)

### Withdraw 

Third-party platforms need to sign tx themselves then broadcast to `radard`; 
  * how to sign a `tx`: [sign-tx](https://radarlab.org/dev/radard-apis.html#sign)
  * Java code reference: [sign-tx-with-java](https://github.com/radrbiz/radarj/blob/master/radar-lib/src/test/java/org/radarlab/test/TestTxn.java)

## Resources 

### Basic 

  * `radarj`: 🌐  <https://github.com/radrbiz/radarj>
  * `radard` doc: 🌐  <https://radarlab.org/dev/radard-apis.html>
  * `radard` transactions doc: 🌐 <https://radarlab.org/dev/transactions.html>
  * `radar RPC tools`: 🌐 <https://info.radarlab.org>
  *  get the chain ledgers info: 🌐 <https://www.radarlab.org/dev-cn/radard-apis.html#ledger-closed>
  * `radard` endpoints:
    * websocket: wss://s1.radarlab.org:5006, wss://s1.radarlab.org:443, wss://s2.radarlab.org:5006, wss://s2.radarlab.org:443 
    * https: https://s3.radarlab.org:443, https://s3.radarlab.org:5005

### API 

#### synchronizing API 

  * API for sync data between Third-party platforms and `radarlab.org`
  * url: 🌐 <https://t.radarlab.org/api/open/syncAccount>
  * Parameters

|Name | Desc|
|-- | --|
|hotwallet | `hotwallet` address of Third-party platform|
|data | sub address list in json format, for example: {"address1": "122.12","address2": "12.1"}|
|sign | md5(data+signKey), signKey is issued by `radarlab.org`|
|pubKey | public key of `hotwallet` [[third-party-access#how to get public key and sign data|how-to-get-public-key]]|
|secretSign   |  keyPair.sign(data) [[third-party-access#how to get public key and sign data|how-to-sign]]|

  * response
  
```
     //Rsponse
     {"status":"success"}
```

#### reliable tx check

Read [reliable-tx](https://radarlab.org/dev/reliable_tx.html) for more information.

`radarlab.org` now provide an API to check the `tx` is successfully applied or not.

  * url: 🌐 <https://t.radarlab.org/api/open/search/{txnHash}>

  * Parameters
	* txnHash string
  * Response

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

### Jave Codes 

#### how to create address 

```
  Wallet wallet = new Wallet();
  String address = wallet.account().address;
  String seed = wallet.seed();
```

#### how to get public key and sign data 

```
	String seed = "snoPBrXt...fg1SUTb"; // seed of address
	String data = "testdatadata"; // data to be signed
	KeyPair keyPair = (KeyPair) Seed.getKeyPair(seed);
	String secretSign = new String(Hex.encode(keyPair.sign(data.getBytes()))); //signed data
	String pubKey = keyPair.pubHex(); // public key
```

### How to Access

Third party who wants to access please send email to <dev@radarlab.org>
