---
title: Radar达成一致共识图解
chapter: 4
order: 6
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# Radar达成一致共识图解

这是关于一致性共识算法的大致图解。

一致性共识的目的是让所有服务器都同意一组交易并生效到最后关闭总账（Last Closed Ledger）上。他们不关心交易是否有效或者交易发生的顺序。他们只关心所有服务器都赞同这组数据是什么。

一致共识是个持续迭代的过程。服务器发出一组交易的提案，然后其他从对端接收到（提案）的服务器也发出自己的提案。

## part 1

这里我们有某一台在Radar网络中的服务器的抽象化图解。

 ![ledger-2](/assets/images/tech/ledger-2.png){:height="600px" width="600px"}
    
在中间显示了关闭包（Closing Bundle）。这是一组交易，网络正在尝试达成一致。

 ![ledger-3](/assets/images/tech/ledger-3.png){:height="600px" width="600px"}
 
现在我们看到，（左上角）一个提案来到了这台服务器。在一致共识达成期间，每个服务器都发出一系列的提案。提案就是 该服务器认为应该把他包含到关闭包里的交易列表，。

 ![ledger-4](/assets/images/tech/ledger-4.png){:height="600px" width="600px"}

（该服务器会对）这传入的提案针对UNL进行检查。如果发送提案的服务器在UNL列表上，那么这个提案被发送到关闭包，并且里面的所有交易都获得1票。

 ![ledger-5](/assets/images/tech/ledger-5.png){:height="600px" width="600px"}

而在网络试图达成在最后一个交易集合的共识(的过程中)，新的交易进入。这些交易被收集在下一包。它们将被施加到下一个总帐（Ledger）。

 ![ledger-7](/assets/images/tech/ledger-7.png){:height="600px" width="600px"}

在这里，我们看到了一个提案，来源服务器不是我们的UNL。这个提案被简单地丢弃，而不用判断什么要包含到最后关闭包里。

## part 2

 ![ledger-8](/assets/images/tech/ledger-8.png){:height="600px" width="600px"}

现在，我们已经得到了来自其他服务器的一些提案。目前我们有5个活跃的UNL服务器。那些被超过50％的活跃服务器投过票的交易，都被认为应该（被服务器）打包。你可以看到标记为绿色的这些交易。

 ![ledger-9](/assets/images/tech/ledger-9.png){:height="600px" width="600px"}

现在，计时器已经用完了，所以我们把我们的针对当前包的投票发送到网络。一个交易是否该放到当前包里，这个（得票率）阈值也从50％提高到60％。这样有很多不同意见的交易，将有一种倾向--被推到下一个总帐。

 ![ledger-10](/assets/images/tech/ledger-10.png){:height="600px" width="600px"}

我们已经收到更多的提案（上图是Server5的新提案到达），改变了我们的想法：关闭包应该包括（哪些交易）。（上图可见“=”这个交易也到达了3/5的投票率）

 ![ledger-11](/assets/images/tech/ledger-11.png){:height="600px" width="600px"}

一致共识机制认为：达到UNL的80% 服务器同意的那些交易，应该放入这个总账。你可以看到在这里发生了，因为每个交易有4个或更多的得票或小于2票。这些交易将被发送并被施加到上次关闭总帐（Last Closed Ledger）。
*译注：这里有个bug？图标为“=”的交易，只有3票，也被发送到LCL了*{: style="color: #800080"}

{{:tech:radar:ledger-12.png?|}}
关闭包开始着手生成新的LCL。你在那个关闭过程中收集到的新交易，将被添加到之前的没能到放总帐的交易候选集里。现在达成一致共识的过程重新开始......

## 补充 

这个文章只说了proposal过程。实际过程比这个复杂，一致性会包括两步，Proposal和Validation；Ledger状态会有三个:
  - ClosingLedger，
  - LCL，
  - AcceptedL。
Proposal阶段会发出自己的closing ledger，大家不断根据收到的proposal建立交集，剩下的建disputed TXs进行投票，投票通过的会继续保留在closing ledger，得票率要求随时间提高，投票不通过的留在下一个ledger处理。

然后就是靠复杂的ContinuousLedgerTiming::haveConsensus() 算法判定何时可以将closing ledger转成LCL并发出validation，之后validation超过quorum个则将LCL转为accepted ledger继续往前走，往后走的过程中一旦发现validation最多的LCL和自己的不一样，则会转入分支切换流程从网络获取新的LCL。

# 相关链接

  * - [一致共识](../consensus)