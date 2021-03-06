---
title: 激活账号
chapter: 4
order: 3
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 激活账号

总账(Ledger)是Radrd的一个核心概念，我们将所有的交易记录，账号变更，余额变动等信息都保存到了总账中。激活一个账号，即表示将账号保存到总账的记录中。至少需要发起一笔交易才能将一个账号记录到总账中。这个过程称作账号激活。

## ActiveAccount

在雷达系统中，我们新引入了一个交易类型：ActiveAccount。该交易用于激活账号操作；雷达系统中已有的账号可以通过发起这个交易，实现转账、激活、增加邀请人三个功能。

## 使用RadrTrade激活一个账号

  * 首先，我们要使用一个已有的radr账号登录到RadrTrade系统中。并选择“转账”；

      ![屏幕快照_2015-05-12_上午11.16.07](/assets/images/ds/屏幕快照_2015-05-12_上午11.16.07.png){:height="200px" width="300px"}

  * 然后输入要激活的雷达地址,此时下方会有提示，未激活账号要多花费0.01VRP的激活费用。

      ![屏幕快照_2015-05-12_上午11.19.44副本](/assets/images/ds/屏幕快照_2015-05-12_上午11.19.44副本.png){:height="300px" width="300px"}

  * 输入金额，进入交易确认页面,输入交易密码确认交易。交易成功后，在交易历史会有一条记录：

      ![屏幕快照_2015-05-12_上午11.27.21副本](/assets/images/ds/屏幕快照_2015-05-12_上午11.27.21副本.png){:height="100px" width="200px"}

  * 整个激活过程就结束了。