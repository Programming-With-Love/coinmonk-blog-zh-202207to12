# 阻碍区块链采用的 4 个智能合约漏洞

> 原文：<https://medium.com/coinmonks/4-smart-contracts-vulnerabilities-that-hinder-blockchain-adoption-6214b6862ad3?source=collection_archive---------23----------------------->

![](img/b92b668525a8b3da83b7c2fb8c76ac39.png)

智能合约只不过是自动运行的代码；当满足预定条件时。它存储在区块链上，使双方能够实时互动，节省大量时间和资源。

智能合同的概念最近获得了极大的关注，因为与传统合同相比，智能合同能够降低成本，提高速度和合规性。

> **智能合约通常被称为区块链协议的主干。尽管非常有用，但它们并不能保证安全。它们有一些严重的缺陷，使它们容易受到恶意攻击。**

在本文中，我强调并解释了智能合约的 4 大漏洞。

# 外部数据源的可靠性

由于智能合约依赖于来自第三方程序的外部信息，这些第三方程序被称为 ***神谕、*** 神谕，因此智能合约极易受到安全威胁。他们不断需要各种加密货币的价格等数据来执行关键功能，如执行保证金通知。

但是对 oracles 的依赖带来了操作风险——比如数据损坏的风险。

# 领跑

在分散式交换中，事务在被包含到块中之前的一小段时间内，在[内存池](https://academy.binance.com/en/glossary/mempool)中是可见的。因此，不良行为者可以利用即将到来的价格波动，以发起这些交易的人为代价获得经济收益，这就是所谓的抢先交易。

> 交易新手？尝试[加密交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)

前跑变得日益复杂，尤其是在 [***Defi、***](https://www.investopedia.com/decentralized-finance-defi-5113835) 中，然而任何人都对此无能为力。

# 重新进入

智能合约使用三个函数将货币转移到外部地址；发送、呼叫和转移。然而，如果目的地址是另一个智能合同，这些函数也充当对指定智能合同中的“后退函数”的函数调用。恶意契约可能会利用这一点创建一个“回退函数”来执行原始契约中的某些内容。

这种攻击可能极具破坏性，因为它们可以完全耗尽智能合约的以太。一个很好的例子是当一个契约使用一个余额变量进行内部核算，并公开它的取款函数。在这种情况下，恶意契约可以反复递归调用取款函数，如果易受攻击的契约在将余额设置为零之前转移资金，它将失去所有资金。

**我们来看一个例子:**

function withdraw()external {
uint 256 amount = balances[msg . sender]；
require(msg . sender . call . value(amount)())；
余额[消息发送者]= 0；
}

# 整数溢出

整数溢出等问题在几乎所有编程语言中都很常见。当有限大小变量的值超过其最大容量时，就会出现整数溢出。发生这种情况时，变量的值会达到其容量的最低值，如下面的代码片段所示:

uint8 数量 _ 用户= 255；

num _ users+= 1；

整数溢出带来的威胁是结果的最高有效位丢失。

# 结论

很明显，智能合同比传统协议有许多优势，如低成本、快速交易、取消中介、更强的控制等。但是智能合约的采用因为它的安全问题而大受影响。

主要问题在于智能合同的复杂性——即使有经验的开发人员在编写完美的智能合同时也会失败。这是由于技术资源不足和固有的[限制，以维持坚实的安全。](https://ethereum.stackexchange.com/questions/305/what-are-common-pitfalls-or-limitations-when-coding-in-solidity)(构建智能合同最常用的语言)

由于它们主要处理金融产品，智能合约必须高度安全。即使智能合约代码中的一个小错误也可能导致数百万美元的损失。因此，除非开发者面临的这些固有问题得到解决，否则区块链似乎很难被视为未来。