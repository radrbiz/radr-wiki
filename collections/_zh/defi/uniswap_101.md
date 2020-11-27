---
title: Uniswap 入门
chapter: 8
order: 3
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}
# Uniswap 入门

Uniswap 是当前最热的 DEFI 项目之一，它是一个运行在以太坊上的去中心化的代币兑换协议，可以为 ETH 和 ERC-20 代币提供流动性服务。

WVBC 是一种发行在以太坊网络的可以与 VBC 进行1比1兑换的 ERC20 代币。关于 WVBC 的介绍和获取方式可以参照文档 [《VBC/WVBC 兑换》](../VBC_WVBC) 。

本文主要介绍如何在 Uniswap 中使用和交易 WVBC。

## ERC20 钱包

要在 Uniswap 进行 WVBC 和其他 ERC20 交易，首先需要有一个 ERC20 钱包，我们推荐你使用MetaMask，本文将以MetaMask为例进行详细讲解。

### 1. 安装并 MetaMask

1. 首先需要安装 Chrome 浏览器，微软 Edge 浏览器，或者 Firefox 浏览器，这里以 Chrome 浏览器为例。

2. 安装 MetaMask 插件，打开网址 [https://metamask.io/download.html](https://metamask.io/download.html)，根据页面的提示安装

    ![](/assets/images/defi/uni101/a01_metamask_download.png)

或者直接打开 Chrome 商店 [Metamask插件页面](https://chrome.google.com/webstore/detail/nkbihfbeogaeaoehlefnkodbefgpgknn)安装。

   ![](/assets/images/defi/uni101/a02_metamask_chrome.png)

### 2. 初始化 MetaMask

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

### 3. 存入WVBC (可选)

如果你想通过 Uniswap 卖出 VBC，你需要将你的 VBC 转换为 VBC 的 ERC20 代币 WVBC，转换的方式参见 [《VBC/WVBC 兑换》](../VBC_WVBC) 一文。

如果你的 `Assets` 资产列表下没有 WVBC，需要将 WVBC 加入资产列表：

1. 点击 `Add Token`

    ![](/assets/images/defi/uni101/a12_metamask_add_token.png)

2. 选择 `Custom Token`

3. 在 `Token Contract Address` 填入 WVBC 的地址 `0x9c088f5b2c4d364447e111d55504eb564f54d184`，MetaMask 将会自动填充其他字段，请确保你看到的信息跟下图是一致的

4. 点击`Next`

    ![](/assets/images/defi/uni101/a14_metamask_custom_token_wvbc.png)

5. 点击`Add Tokens`即可将 WVBC 加入资产列表

    ![](/assets/images/defi/uni101/a15_metamask_custom_token_wvbc1.png)

6. 此时将在你的资产列表中显示 WVBC 条目

    ![](/assets/images/defi/uni101/a18_metamask_token_list.png)

### 4. 存入 ERC20 代币 (可选)

如果你想通过 Uniswap 买入 VBC 或想向 Uniswap 资金池注入流动性来获取收益，你需要向钱包冲入 你想参与的 Uniswap 货币对的对应 ERC20 代币 (比如USDT)。

存入的方法与存入 ETH 或者 WVBC 的方式类似，按照你熟悉的方法存入即可。

### 5. 存入少量 ETH

Uniswap 是基于以太坊 (Ethereum) 的 DEFI 应用，在 Uniswap 进行任何交易，都需要消耗少量的 ETH 作为手续费 (gas)，所以我们需要存入少量的 ETH 到 MetaMask 钱包才能进行 Uniswap 的交易。

1. 首先，找到你的钱包的 ETH 地址，点击 MetaMask 页面中你的账户名称，页面将自动复制你的 ETH 地址到剪贴板

    ![](/assets/images/defi/uni101/a25_metamask_copy_address.png)

2. 你可以通过多种方式转账ETH到你的 MetaMask 钱包：
     1. 从你的其他ETH钱包直接转账
     2. 如果你在雷达钱包有ETH余额，可以选择提币到你的MetaMask钱包的地址
     3. 如果你在其他交易所有ETH的余额，可以在交易所的提币到你的MetaMask钱包的地址
3. 提币转账操作需要等待以太坊网络确认交易，所以需要等待一段时间才能在钱包看到你的ETH余额。

## 链接钱包和 Uniswap

可以通过网址 [https://app.uniswap.org/](https://app.uniswap.org/) 打开Uniwap交易页面。在进行任何类型的操作之前，需要将 Uniswap 链接到你的钱包。

1. 点击 `Connect to a wallet`按钮

    ![](/assets/images/defi/uni101/a19_uniswap_connect_to_wallet.png)

2. 在弹出的列表中选择 `MetaMask`

    ![](/assets/images/defi/uni101/a20_uniswap_wallet_list.png)

3. MetaMask 插件将会弹出一个对话框，点击`Next`

    ![](/assets/images/defi/uni101/a21_uniswap_metamask.png)

4. 点击`Connect`

    ![](/assets/images/defi/uni101/a22_uniswap_metamask1.png)

5. 稍等片刻，即可连接成功

    ![](/assets/images/defi/uni101/a23_uniswap_metamask_doing.png)

    ![](/assets/images/defi/uni101/a24_uniswap_metamask_done.png)

## 兑换 WVBC

Uniswap 支持任意一对支持 Uniswap ERC20 代币对之间的兑换，本节为不熟悉 Uniswap 的用户讲解兑换 WVBC 的基本操作步骤。

1. 在 Uniswap 中选择 `Swap` 选项卡
2. 选择要兑换的代币对，如果没有 WVBC，可在在搜索框中填入 WVBC 的合约地址 `0x9c088f5b2c4d364447e111d55504eb564f54d184` 查找，搜索到 WVBC 之后可以点击  Add 将其添加到常用列表中，下次 WVBC 将直接显示在列表中

    ![](/assets/images/defi/uni101/a26_uniswap_add_wvbc.png)

3. 同样方法将兑换的对应代币（如USDT）加入到列表中
4. 选择好兑换的代币对，并选择兑换的方向(如USDT→WVBC或者WVBC→USDT等)，填入兑换的数额，只填入其中之一即可，另一方的价格会根据当前价格自动计算。

    ![](/assets/images/defi/uni101/a30_uniswap_do_swap.png)

5. 如果是首次操作某种代币，将会看到如下页面，需要先进性授权操作，如果不是，直接跳转到步骤 8

    ![](/assets/images/defi/uni101/a27_uniswap_swap.png)

6. 点击 `Approve WVBC` 进行授权，此时会唤起 MetaMask插件进行签名并授权并发送交易

    ![](/assets/images/defi/uni101/a29_uniswap_approve_waiting.png)

7. 等待 `Approve` 交易确认
8. 确认好价格和数量之后，点击`Swap`按钮，在确认页面点击 `Confirm Swap`, 会唤起MetaMask插件进行签名授权并发送交易

    ![](/assets/images/defi/uni101/a31_uniswap_confirm_swap.png)

    ![](/assets/images/defi/uni101/a32_uniswap_sign_swap.png)

    ![](/assets/images/defi/uni101/a33_uniswap_send_swap.png)

9. 代交易确认后，即可在MetaMask钱包查看到兑换所得的代币余额

## 增加流动性

Uniswap 支持流动性挖矿，用户可以通过向 Uniswap 注入流动性来获取后续的兑换手续费的分成，借此来获得收益。

由于获得收益是代币的形式，而代币的价格是浮动的，所以用户应该在充分理解 Uniswap 的流动性挖矿机制的前提下参与挖矿，以免造成不必要的损失。

1. 选择 `Pool` 选项卡，并选择 `Add Liquidity`

    ![](/assets/images/defi/uni101/a34_uniswap_pool.png)

2. 选择要增加流动性的代币对(如WVBC/USDT)，如果没有找到对应的代币，首先参照上一章中的步骤 2 的方法进行添加
3. 填入要兑换的数额，只需填入其中一种，另一种会按照资金池的代币比例自动计算

    ![](/assets/images/defi/uni101/a35_uniswap_add_liquidity.png)


4. 如果代币对中有没有授权的代币，请参照上一章步骤 5 - 7 进行授权
5. 点击 `Supply`，在在确认页面点击 `Confirm Supply`, 会唤起MetaMask插件进行签名授权并发送交易

    ![](/assets/images/defi/uni101/a36_uniswap_add_liquidity1.png)

    ![](/assets/images/defi/uni101/a37_uniswap_add_liquidity2.png)

6. 代交易确认后可以在 `Pool` 页面看到参与的流动性池的列表，在此你可以查看自己在此代币对池的概况

    ![](/assets/images/defi/uni101/a41_uniswap_pool_list.png)

7. 如果没有显示上图列表，可以手动导入

   * 在下图页面点击`Import it`
   
	![](/assets/images/defi/uni101/a39_uniswap_pool_import.png)
	
   * 选择代币对，并点击`Manage this pool` 将代币对池加入列表
   
	![](/assets/images/defi/uni101/a40_uniswap_pool_usdt_wvbc.png)


## 移除流动性

如果用户想退出流动性挖矿拿回注入的资金，则需要进行流动性移除操作。移除流动性会根据当前的价格退还用户抵押的代币。需要注意的是，由于 Uniswap 的原理，矿池中的资金量比例变化会引起价格的变化，实际退还用户的代币额度不一定跟用户当初抵押的额度相同。

1. 选择 `Pool` 选项卡，并在 `Your liquidity` 列表下找到要移除流动性的代币对，如果没有，参照上一章步骤 7 来添加

    ![](/assets/images/defi/uni101/a41_uniswap_pool_list.png)

2. 点击 `Remove` 按钮，并在 `Remove Liquidity`页面选择要移除的比例，该页面会大致计算移除后可赎回的两种代币的数量

    ![](/assets/images/defi/uni101/a42_uniswap_pool_remove.png)

3. 点击 `Approve`，会唤起MetaMask插件进行签名授权并发送交易

    ![](/assets/images/defi/uni101/a43_uniswap_pool_remove_sign.png)

4. 等待交易确认，即完成流动性移除操作，赎回的代币余额可以在MetaMask钱包中查看

## 免责声明

1. 当 VBC 转换为 WVBC 之后，会进入以太坊网络中流通，雷达网络对流通在以太坊网络的 WVBC 不会也没有能力进行干预，用户需要在充分了解以太坊网络的运行机制的前提下使用 WVBC。
2. Uniswap 是一个运行在以太坊上的公开的 DEFI 项目，雷达并不参与 Uniswap 的开发与运行维护工作。用户所有涉及到 WVBC 的 Uniswap 操作，都被认为是在充分了解 Uniswap 的原理以及风险的情况下进行，因此而产生的任何收益和损失均与雷达无关。
3. 本文中提到的 MetaMask 钱包与雷达没有任何利益关联，用户需要充分了解其原理及使用风险，雷达对因使用该钱包产生的任何问题都不负责。



