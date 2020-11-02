---
title: MoneyMail 说明
chapter: 1
order: 6
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# MoneyMail 说明

  * 在转账栏直接给邮箱地址转账；

    ![MoneyMail2-cn](/assets/images/money_mail/MoneyMail2-cn.png){:height="300px" width="300px"}

  * 在账号注册邮箱直接给另外一个邮箱转账
  * 接收人分为以下四种情况
    * 邮箱未注册
    * 邮箱已注册，但未激活
    * 邮箱已注册已激活，但账号未激活
    * 邮箱已注册已激活，账号已激活

其中，后两种情况按之前给账号的转账逻辑执行；前2种则会触发MoneyMail.


## 转账栏给邮箱转账

### 规则

  * 邮箱转账的货币为官方货币集合: CNY,BTC,ETH,VBC,VRP,XRP,EOS,BCH
  * 邮箱已注册已激活，但账号未激活 的逻辑和激活账号并转账的逻辑一致；
  * 邮箱已注册已激活，账号已激活 的逻辑和普通转账一致；
  * 转账非VRP货币时，第一个下发转账的账号需要给对方附加 0.01VRP 作为交易手续费；
  * 用户在给邮箱转账后会先行扣除转账所需资产和 费用: 扣费规则请见下方 转账费用计算；
  * 转账有效期1周，超时资产将被退回（备注: 所有VRP费用无法退还)；
  * 扣除费用成功之后，将会给接收邮箱发送邮件，并附上转账接收链接；
  * 用户点击接收链接后，会跳转到接收页面，用户需要注册账号之后领取资产；
  * 用户注册成功之后，邮箱将被自动标记为已激活，无需再次激活；
  * 用户注册成功之后，之前的资产会自动下发；用户登录以后可以在首页看到自己待接收的资产列表；

## 通过发送电子邮件转账

### 规则

  * 首先，账号需要在设置页面开通邮箱内转账的功能并设置单日转账上限(备注：各种货币根据实时价格换算为CNY价值)，如下图

    ![settings-money-mail-cn](/assets/images/money_mail/settings-money-mail-cn.png){:height="200px" width="150px"}

  * 邮箱转账的货币为官方货币集合: CNY,BTC,ETH,VBC,VRP,XRP,EOS,BCH
  * 在邮箱内的email格式为
    * 标题：发送的数量+空格+发送的货币, 例如: 200 CNY
    * 需要抄送 mm@radarlab.org

    ![mmail2-cn](/assets/images/money_mail/mmail2-cn.jpg){:height="300px" width="300px"}

  * 邮箱已注册已激活，但账号未激活 的逻辑和激活账号并转账的逻辑一致；
  * 邮箱已注册已激活，账号已激活 的逻辑和普通转账一致；
  * 转账非VRP货币时，第一个下发转账的账号需要给对方附加 0.01VRP 作为交易手续费；
  * 用户在给邮箱转账后会先行扣除转账所需资产和 费用: 扣费规则请见下方 转账费用计算；
  * 转账有效期1周，超时资产将被退回（备注: 所有VRP费用无法退还)；
  * 扣除费用成功之后，将会给接收邮箱发送邮件，并附上转账接收链接；
  * 用户点击接收链接后，会跳转到接收页面，用户需要注册账号之后领取资产；
  * 用户注册成功之后，邮箱将被自动标记为已激活，无需再次激活；
  * 用户注册成功之后，之前的资产会自动下发；用户登录以后可以在首页看到自己待接收的资产列表；

##  MoneyMail列表

通过在转账页面 🌐 <https://t.radarlab.org/transfer> 的交易历史最后的分类选择可以查看MoneyMail历史

  ![transfer-cat-cn.png](/assets/images/money_mail/transfer-cat-cn.png){:height="200px" width="200px"}

## 转账费用计算

中间账号设置转账激活无需费用. 每次email转账固定费用0.011VRP.

### 首笔费用 

  * 转账VRP, 无需附加0.01VRP手续费
    
    ```
    fee=Math.max((amount+0.011)/1000, 0.001) + 0.011(MoneyMail) VRP
    ```

  * 转账VBC，附加0.01VRP手续费
    
    ```
    fee = Math.max(amount/1000, 0.001) + 0.01(附送手续费) + 0.011(MoneyMail) + 0.001(本次转账0.01VRP手续费) = 0.022 + Math.max(amount/1000, 0.001) VRP
    ```

  * 转账其他资产
    
    ```
    fee = 0.001(资产转账fee) + 0.01(附送手续费) + 0.011(ActiveAccount) + 0.001(VRP手续费) ) = 0.023 VRP
    ```

### 非首笔费用 

  * 转账VRP, 无需附加0.01VRP

    ```
    fee = Math.max((amount+0.011)/1000, 0.001) + 0.011(MoneyMail) VRP
    ```

  * 转账VBC

    ```
    fee= Math.max(amount/1000, 0.001) + 0.011(MoneyMail) + 0.001(转账VRP手续费) VRP
    ```

  * 转账其他资产

    ```
    fee=0.001(资产转账fee) + 0.011(MoneyMail) + 0.001(转账VRP手续费) = 0.013 VRP
    ```




