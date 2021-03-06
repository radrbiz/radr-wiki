---
title: 交易费用说明
chapter: 1
order: 3
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 交易费用说明

所有的去中心化的、基于加密技术的数字货币（虚拟货币），都是公开总账的。为了维持公开总账的稳定，防止被人恶意攻击，发出大量无效的交易，浪费资源，交易系统都会对所有的交易收取一定的手续费。手续费对正常交易的人而言是非常低的。在雷达系统里，是通过消耗VRP（本身也是一种可以自由购买的虚拟货币）来实现交易费。

  - 钱包激活（创建账号）：需要有人转账给新地址，收发起人0.01 VRP + 转账交易费（见2）
  - 转账交易费：
    - VBC、VRP两种货币转账：收发起人 (交易金额 * 1/1000) VRP，最低0.001VRP作为交易费；
    - 其它货币转账：固定交易费  0.001 VRP
    - Offer等其它交易类型：固定交易费  0.001 VRP
  - 钱包保底余额：没有要求，即，已被激活的地址里，可以把余额全部转移出去
  - 需要注意，一旦钱包里VRP余额为0了，将不能再发起任何新的交易，只能等到别的账号给他转账VRP！
  
# 相关链接
   * [英文版](/en/introduction/transaction_fee)
   * [Radar百科](/zh)
   * [新币发行分配算法](../../tech/dividend)
