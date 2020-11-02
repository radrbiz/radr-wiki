---
title: 理解“资金流转”标记
chapter: 4
order: 5
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 理解“资金流转”标记

“资金流转”标记是雷达信任链的一个设置项，当一个账号在两个信任链上设置了“资金流转”标记，第三方的交易就不能通过这个账号在这些信任链上进行资金流转。如果一个做市商信任了同一币种的不同发行者，这个设置能够保证它的余额不会意外地在不同发行者之间发生流转。

## 背景
“Radaring”发生在设置了多于一条信任链的交易中。比如，Alice欠Charlie钱，同时Alice也欠Bob的钱，我们可以用下图来表示他们之间的信任关系：

![noripple-01](/assets/images/ds/noripple-01.png)

如果Bob想要支付$3给Charlie，他可以这样说：“Alice，把你欠我的钱中的$3支付给Charlie”。Alice只是简单地把她欠Bob的部分债务转移到Charlie那里。最终的信任关系变成下面的样子：

![noripple-02](/assets/images/ds/noripple-02.png)

我们把这种两个账号借助彼此间的信任链来流转资金达成易的过程叫做“Radaring”（资金流转），这是雷达的一个重要的特性。“Radaring”发生在账号之间被信任了同一币种的信任链连接的情况。只要求货币代号完全相同，而并不要求其发行者是同一个（事实上，长的信任链本身就要求发行者是不同的）。

## 缘由
有时候你并不希望你的资金发生流转。比如，Emily在两个不同的网关都有存款，像下面这样：

![noripple-01](/assets/images/ds/noripple-03.png)

现在Charlie想通过Emily的账号的流转功能来支付给Daniel $10：

![noripple-04](/assets/images/ds/noripple-04.png)

这可能让Emily感到意外，因为她既不认识Charlie也不认识Daniel。如果网关A的提现费率比网关B高的话，这将会让Emily支付更多的费用。“资金流转”标记是信任链的一项设置，如果你在两条信任链上都设置了这个标记，交易就不能通过你的账号在这两条信任链上流转了。

例如：

![noripple-05](/assets/images/ds/noripple-05.png)

上面这种情况，Charlie就无法利用Emily的账号的流转功能来支付给Daniel了。

## 详细说明
某些路径会因为“资金流转”标记而失效，使得无法通过它们来达成交易。一个路径中如果包含了一个设置了“禁止资金流转”的账号节点，并且这个节点是一个中间节点，那么这条路径就被认为是无效的。

![noripple-06](/assets/images/ds/noripple-06.png)

## 技术细节

### 打开/关闭 资金流转 标记

“资金流转”标记只有在账号在相应的信任链上有大于或等于零的余额的时才能够被设置。这样就使得该特性不会被滥用，导致信任链拒绝履行它应尽的义务（当然，你依然可以通过放弃账号的方式来做到这一点）。

在WebSocket/JSON-RPC API中，你可以通过发送带有tfSetNoRadar标记的TrustSet交易来打开“资金流转”标记，或者发送带有tfClearNoRadar标记的TrustSet交易来关闭它。

在Radar-REST API中，你可以通过Grant Trustline方法来开关“资金流转”标记。如果account_allows_radaring字段设置为true，“资金流转”标记就被关闭了；反之，如果account_allows_radaring字段设置为false，“资金流转”标记就被打开了。

在Radar Trade客户端中，资金流转（Radaring）是信任链的一个高级设置项。信任链的高级设置可以通过点击信任→网关列表→资金流转→开启。当信任链的特性显示的时候，可以通过选中和取消选中“Radaring”选项来进行设置，如下图：

![trust](/assets/images/ds/trust.png)

### 查看“资金流转”状态


在两个账号彼此之间都设置了信任的情况下，每个账号的“资金流转”标记是分别设置的。

在WebSocket/JSON-RPC APIs中，可以通过account_lines方法来查看账号的信任链。对于每一条信任链，no_radar布尔值标识了当前账号是否在这条信任链上设置了“NoRadar”标记，no_radar_peer则标识了对方是否在这条信任链上设置了“NoRadar”标记。

在Radar-REST API中，可以通过Get Trustlines方法来查看账号的信任链信息。对于每一条信任链，如果account_allows_radaring字段为true，那么“资金流转”标记就是关闭的，反之就是打开的。

在Radar Trade客户端中，你可以在设置打开/关闭“资金流转”标记的地方查看这一状态，里面会有叫做Radaring的一列，其内容是on或者off，分别对应“radaring”的打开和关闭状态。
