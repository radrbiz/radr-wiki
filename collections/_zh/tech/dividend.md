---
title: 新币发行分配算法
chapter: 3
order: 1
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# 新币发行分配算法

系统内置的VBC，是每日新增发行的，发行数和比特币类似，定期衰减。目前，每日发行新VBC比率是发行时刻总数的 0.10%(自2018-1-7起) 。

发行收益发放根据两部分确定：持有VBC的余额排名；推广算力。 下面是具体算法：

## 一、持币排名发行

$$VRATE=USERi/\Sigma_{i=1}^nUSERi$$

账号余额（持币量）的排名（多账号可能同名次，但是下一名次同步跳跃增长），作为该部分发行的权重。

## 二、推广发行

![div2](/assets/images/tech/div2.png)

下图中

* T(累积持币量) == 上图公式中的 AMTj，
* T在有的地方也表示为“TSPRD”
* B代表账号的VBC余额

![div-cn](/assets/images/tech/div-cn.png)

***相关链接***

* [Radar百科](/zh)
* [交易费用说明](../../introduction/transaction_fee)
* [新币发行分配算法英文版](/en/tech/dividend)
