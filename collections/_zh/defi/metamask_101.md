---
title: MetaMask 入门
chapter: 8
order: 4
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# MetaMask 入门

MetaMask 是一个简单易用的 ETH 钱包，在桌面端它以浏览器插件的形式运行，在移动端，可以安装 MetaMask 钱包 APP。本文以桌面端为例，介绍 MetaMask 的基本的安装和使用方法。

## 1. 安装 MetaMask

1. 首先需要安装 Chrome 浏览器，微软 Edge 浏览器，或者 Firefox 浏览器，这里以 Chrome 浏览器为例。

2. 安装 MetaMask 插件，打开网址 [https://metamask.io/download.html](https://metamask.io/download.html)，根据页面的提示安装

    ![](/assets/images/defi/uni101/a01_metamask_download.png)

或者直接打开 Chrome 商店 [Metamask插件页面](https://chrome.google.com/webstore/detail/nkbihfbeogaeaoehlefnkodbefgpgknn)安装。

   ![](/assets/images/defi/uni101/a02_metamask_chrome.png)

## 2. 初始化 MetaMask

1. 首次使用 MetaMask 插件，需要进行初始化，点击 `Get Started`

    ![](/assets/images/defi/uni101/a03_metamask_get_started.png)

2. 如果你已经有密钥短语，可以通过导入密钥短语的方式进行初始化，这里假设你没有密钥短语，点击 `Create a Wallet`

    ![](/assets/images/defi/uni101/a04_metamask_create_a_wallet.png)

3. 在 `Help Us Improve MetaMask` 页面点击 `No Thanks` 或者 `I Agree` 均可，取决于你是否希望共享非敏感数据给 MetaMask 来改进用户体验

    ![](/assets/images/defi/uni101/a05_metamask_agreement.png)

4. `Create Password` 页面需要你指定钱包的密码，至少需要8个字符，这个密码在操作钱包时会用到，请保证密码的强度，并妥善保管

    ![](/assets/images/defi/uni101/a06_metamask_new_password.png)

5. `Secret Backup Phrase` 这里会提示你保管种子秘钥短语，在确保安全的环境下点击 `CLICK HERE TO REVEAL SECRET WORDS`来显示密钥，通过安全的方式 (比如可以写在纸上放进你的保险柜里) 记录这些短语。**注意，这是恢复你的钱包账户的唯一依据，拥有这些短语的人可以通过这些短语恢复你的钱包并操纵其中的资产**

    ![](/assets/images/defi/uni101/a07_metamask_backup_phrase.png)

    ![](/assets/images/defi/uni101/a08_metamask_backup_phrase1.png)

6. 在 `Confirm your Secret Backup Phrase` 页面按照上一步记录的顺序依次点击单词，来确认你的秘钥短语

    ![](/assets/images/defi/uni101/a09_metamask_confirm_phrase1.png)

7. 在 `Congratulations` 页面点击 `All Done`，你的钱包就创建完毕了

    ![](/assets/images/defi/uni101/a10_metamask_all_done.png)

## 3. 存入少量 ETH

任何基于以太坊 (Ethereum) 的 DEFI 应用，在发送任何交易时，都需要消耗少量的 ETH 作为手续费 (gas)，所以我们需要存入少量的 ETH 到 MetaMask 钱包才能通过 MetaMask 发起任何交易。

1. 首先，找到你的钱包的 ETH 地址，点击 MetaMask 页面中你的账户名称，页面将自动复制你的 ETH 地址到剪贴板

    ![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

2. 你可以通过多种方式转账ETH到你的 MetaMask 钱包：
     1. 从你的其他ETH钱包直接转账
     2. 如果你在雷达钱包有ETH余额，可以选择提币到你的MetaMask钱包的地址
     3. 如果你在其他交易所有ETH的余额，可以在交易所的提币到你的MetaMask钱包的地址
3. 提币转账操作需要等待以太坊网络确认交易，所以需要等待一段时间才能在钱包看到你的ETH余额。

## 4. 存入 ERC20 代币

[ERC20](https://eips.ethereum.org/EIPS/eip-20) 是以太坊网络中的一种通用的代币接口标准。通过 ERC20 协议来接收或者发送代币是一种是非常常见的操作。

### 添加代币到钱包

如果你希望发送或接收的代币没有出现在你的代币列表，则需要手动添加。
1. 点击 `Add Token`

    ![](/assets/images/defi/uni101/a12_metamask_add_token.png)

2. 如果要添加的代币是常见代币，选择 `Search`，输入代币的名称，从列表中点击要选择的代币，点击 `Next`，然后点击`Add Tokens`即可将该代币加入资产列表
3. 如果要添加的并非常见代币，选择 `Custom Token`，在 `Token Contract Address` 填入代币的合约地址，MetaMask 将会自动填充其他字段，你看到的信息跟下图类似

		![](/assets/images/defi/uni101/a14_metamask_custom_token_wvbc.png)

点击`Next`，点击`Add Tokens`即可将 代币 加入资产列表

    ![](/assets/images/defi/uni101/a15_metamask_custom_token_wvbc1.png)

### 接收代币

接收代币很简单，只要你的 ETH 地址发送给发送代币的人就可以了，找到你的钱包的 ETH 地址，点击 MetaMask 页面中你的账户名称，页面将自动复制你的 ETH 地址到剪贴板

    ![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

将这个地址通过任何方式发送给发送代币的人，对方就可以向你发送代币了。

### 发送代币

1. 在代币列表中选择要发送的代币
2. 点击 `Send`
3. 在输入框输入接收人的 ETH 地址
4. 在 `Amount`，一拦填入发送的数量
5. 点击 `Next`
6. 点击 `Confirm`



