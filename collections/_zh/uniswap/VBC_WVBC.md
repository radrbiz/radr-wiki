---
title: VBC/WVBC 兑换
chapter: 8
order: 2
layout: default.zh
lang: zh
---

# VBC/WVBC 兑换

目前大多数的基于以太坊的 DEFI 应用都是基于 ERC20 协议来运行的。为了让雷达充分的参与和利用 DEFI 生态， 我们引入了一种新的基于以太坊的 ERC20 代币 WVBC (Wrapped VBC)，以及一个支持雷达代币 VBC 和 WVBC 相互兑换的兑换系统。

兑换为 WVBC 代币后，用戶可以在以太坊网络的各类基于 ERC20 的 DEFI 应用(如 Uniswap 等)中进行 VBC 交 易。

本文主要介绍什么是 WVBC，以及如何在 VBC 和 WVBC 之间进行兑换。 

## 1. 什么是 WVBC

WVBC  (Wrapped VBC) 是一种发行在以太坊网络的可与 VBC 进行 1 比 1 兑换的 ERC20 代币。 

雷达网络提供了一个自动兑换系统，该系统对应一个公开可审计的雷达账戶，账户地址为:

```
rsVeqrYjJbYMdar7A6c4EyscZ4WgbY92ys
```

我们称该账戶为**质押账戶**，以太坊上的每一枚 WVBC 代币都对应一枚质押并冻结在**质押账戶**的 VBC，质押账戶的 VBC 余额公开可审计，并严格保证如下条件:

```
质押账戶 VBC 余额 ≥ WVBC 流通总量
```

将 VBC 兑换为 WVBC，要经过如下步骤:

1. 用戶指定接收 ERC20 代币的以太坊地址，并向雷达网络的质押账戶转入指定额度 VBC
2. 兑换系统监测转入质押账戶的 VBC，通过 ERC20 代币合约向用戶指定的接收 ERC20 代币的以太坊地址转入对应额度的 WVBC

将 WVBC 兑换为 VBC，要经过如下步骤:

1. 兑换系统为每个用戶生成不同的 WVBC **兑回地址** (也是一个以太坊地址)
2. 用戶将指定额度的 WVBC 通过 ERC20 转账操作转入到自己的 WVBC **兑回地址**
3. 兑换系统监测转入到用戶**兑回地址**的 WVBC 代币，将对应额度的 VBC 从**质押账戶**解冻并转入到用戶的雷达账户，同时调用 ERC20 合约的销毁接口销毁对应额度的 WVBC

以上是 WVBC 的原理及技术实现方案，事实上，作为不关心技术细节的终端用戶，实际的操作流程会相对简单，接下来的两小节将会从用戶的⻆度来介绍 VBC 和 WVBC 的兑换流程。

## 2. VBC 兑换为 WVBC

1. 在`概览`⻚面的`VBC`区块下点击`转换 WVBC` (图1)

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v01_convert_wvbc.png)

    图 1

2. 选择 转换`VBC→WVBC` (图2)
3. 填入用戶的 ERC20 代币充值的以太坊地址(图2) 
4. 填入要兑换的`VBC`数量(图2)
5. 点击`确认`(图2)
6. 兑换历史可以在`转换VBC记录`区块(图2)查看

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v02_to_wvbc.png)

    图 2 

注意事项:

1. 兑换过程会在以太坊网络产生手续费，兑换系统会统一折算成 VBC 在雷达网络收取，用戶实际 收到的 WVBC 为扣除手续费之后的额度
2. 为了避免小额兑换造成不必要的手续费损耗，兑换系统要求兑换的最小额度为 10 VBC
3. 转换过程需要首先等待雷达网络交易确认，然后等待以太坊网络的交易确认，所以需要等待一段时间才能完成

## 3. WVBC 兑换为 VBC

1. 在`概览`⻚面的`VBC`区块下点击`转换WVBC` (图1)
2. 选择`转换WVBC→VBC`(图3)

    ![switch-wvbc-zh](/assets/images/uniswap/wvbc/v03_to_vbc.png)
    
    图 3

3. 复制`WVBC`**兑回地址**(图3)
4. 将复制的**兑回地址**填入 ERC20 钱包的转账目标地址中，并向该地址转入指定额度的 `WVBC`代币
5. 兑换完成后，兑换历史可以在 转换`WVBC`记录 区块(图3)查看

注意事项:

1. 兑换过程会在以太坊网络产生手续费，WVBC转账的手续费(gas)由用戶的 ERC20 钱包收取，其余手续费(如 WVBC 销毁 gas)兑换系统会统一折算成 WVBC 收取，用戶实际收到的 VBC 为扣除手续费之后的额度

2. 兑换系统要求最小的兑换额度为 1 VBC，小于 1 的 WVBC 转账将会被忽略，且不会退还

3. 兑回的 WVBC 转账操作在用戶的 ERC20 钱包进行，雷达网络不参与该过程，所以用戶一定要保证输入的**兑回地址**正确，输入地址错误将造成 WVBC 代币丢失且无法找回

4. 转换过程需要首先等待以太坊网络的交易确认，然后等待雷达网络的交易确认，所以需要等待一段时间才能完成
