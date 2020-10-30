---
title: RADR介绍
layout: default.zh
lang: zh
permalink: /zh/
---
*  目录
{:toc}

# RADR百科

## 简介

雷达（RADR, 🌐 <https://radarlab.org/cn/>）是基于Ripple的RTXP协议的金融网络产品。它促进和开发了全球化的、更快速、低成本的支付、清算系统，汇兑系统。它支持各种类型的货币，使得互联网支付就像Email一样简单便捷。

特别的，VRP、VBC都是在RADR网络里的内置原生货币。 VRP主要用来作为交易费，防止垃圾交易；而VBC是创新引入的“社交货币”。RADR核心程序会按照特定的持币量和推广关系算法，每日发行新货币，以促进RADR推广者的收益并产生动力。

不像一些传统的银行机构，基于RTXP协议的RADR 的分布式网络提供全网共享的公共总账，其意味着任何在RADR网络内的电子交易都是公开透明、即时有效，不会被任何组织或机构控制的。RADR的服务端、客户端代码都是开源的，在下文地址里，任何人都能复制代码，在自己的服务器上运行RADR程序。使用RADR是免费的，RADR属于全体参与者共同拥有，不被任何中央机构所控制，是个去中心化的金融产品。

关于RADR的详细介绍，请阅读《[RADR介绍](./introduction/introduction)》。

|项目和产品| 相关文档|
| --- | --- | 
|1、RADRInfo: 🌐 [RADR实时动态数据](https://info.radarlab.org/ledger_list.html) (如：Ledger, Tx, Account...) | |
|2、RADRTrade: 🌐 [RADR交易平台(官方平台)](https://t.radarlab.org/index.html) | [交易平台帮助](./introduction/trade_help)  <br> [新钱包使用帮助](./introduction/trade_help) <br> [冷钱包使用说明](./tech/cold_wallet) |
|3、RADRCharts: 🌐 [交易所K线图](https://charts.radarlab.org/) | |
|4、雷达客户端：🌐  [iOS和Android客户端](https://www.radarlab.org/cn/download.shtml) | |
|5、开发文档：🌐 <https://radarlab.org/dev/> | |

## 技术细节

| | 相关文档 |
| --- | --- | 
|技术细节| [发行新币算法说明](./introduction/dividend) <br> [账号（Account）](Account) <br> 解决[双重支付问题](double-spending)的一种方法 |
|关键角色| [网关介绍](./gateway/start) <br> [做市商](./marketmaker/start) |
|开源代码 | 1、Server端 源码: https://github.com/radrbiz/radard <br> 2、Java Client: https://github.com/radrbiz/radarj <br> 3、冷钱包：https://github.com/radrbiz/radar-wallet | 

## 其它特性说明
### 遵循网络共识的交易机制
RADR网络上的共享总账是由全体分布式服务器共同管理的。不同于传统的中心化网络操作，遍布RADR网络的分布式服务器遵循先进的相互共识算法来认可共享总账上的变化。而为了改变总账的数据，每次共识必须被全网绝大部分连接的服务器所认可，然后服务器可依据此更新自己本地数据库的副本，若当前交易的此次全网共识未能达成，交易条目会被驳回，于是任何时候所有用户都对共享总账的认知一致。


### 基于数学的货币
基于数学的货币是指具有可以被验证的数学特征的电子资产。基于数学的货币本身如同传统法定货币一般具备价值等资产性质，其可以在没有中央管理者的分布式网络中自由流通与交易。

在RADR 网络中，存在了两种发行于网络存在之始的原生的基于数学的电子货币，VRP和VBC。由于基于数学的货币供给量是由数学定理决定的，规则之外没有给予人为操纵的空间。

类似比特币一样，基于RTXP的RADR 网络让处于分布式网络的全网用户能够点对点的进行货币交易与即时结算。这极大的减少了跨行转账，特别是国际转账过程中所带来的风险与手续费用。

## 交易费用说明

[各项费用说明](/Transaction_Fee)

## 版权License

RADR是开源的系统，遵循 ISC 协议. 详情查看上面开源地址里的 LICENSE 文件.

## 联系我们

| 名称 | Emails |
| --- | --- | 
|客户服务 | <radar@radarlab.org> |
|开发者帮助 | <dev@radarlab.org> |
|网关申请 | <dev@radarlab.org> |

## 在线支持
在线支持，请添加Skype（[官网下载](http://skype.gmw.cn/down/|官网下载)）好友：radrservice

## 本文其他语言
    - [RADR英文]
