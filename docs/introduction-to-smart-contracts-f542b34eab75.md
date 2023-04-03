# 智能合同简介

> 原文：<https://medium.com/coinmonks/introduction-to-smart-contracts-f542b34eab75?source=collection_archive---------19----------------------->

![](img/c6715766b5d338392a7541328597f9f5.png)

> 你可以在这里阅读我上一篇关于“为什么是以太坊”的文章👇

 [## 以太坊解决的区块链局限性…

### 你可以阅读我上一篇关于区块链如何进行交易的文章..这里👇

medium.com](/coinmonks/limitations-of-blockchain-solved-by-ethereum-e904fecfd50a) 

让我们开始…

💜真实世界的合同
纸质合同已经在世界上出现了。那么，我们为什么需要智能合同呢？我们当前的合同存在一个问题

-纸质合同基本上是由政府支持的。人们相信，如果合同协议没有得到履行，他们可以向政府投诉。
-但是如果政府不支持会怎么样？如果政府突然做出改变，你的合同失效，你该怎么办？
——现在没人能做什么了。

那么解决办法是什么呢？….

> 交易新手？尝试[加密交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)

💜**智能合约**
——智能合约是用 solidity 编写的电子合约，然后部署到 EVM(以太坊虚拟机)。
-智能合约就像一个不能违背的承诺。

💜**工作原理**
我们已经看到了区块链和以太坊的工作原理。就像银行账户一样，我们在以太坊也有账户。
-现在我们在银行有了独一无二的账号。同样，我们有唯一的帐户地址。我们在银行账户上有余额。同样，我们的账户也有余额。

现在，以太坊处理智能合约的方式类似……
-当我们将智能合约部署到以太坊时，它也被视为链上的一个账户。
-以太坊为智能合约提供其唯一的地址、自己的余额以及其他账户使用已部署智能合约的能力。
——这些智能合约生活在链条上，一旦满足某个条件，它就执行相应的功能。

因此，我们可以看到，任何外部权威或任何人都可以改变或使合同无效。

> 👉请记住，智能合约一旦部署在链上，就不能被更改/改变，因为链使更改变得太难。我们可以阻止/允许访问，但我们不能改变它。

💜**智能合约的应用**
它可以用来创建这些……
-DeFi->去中心化财务
- DAOs - >去中心化自治组织
- NFTs - >不可替换令牌
- Dapps - >去中心化应用

💜EVM 如何处理智能合同
——智能合同是用 solidity 编写的，solidity 是一种深受 JavaScript 启发的编程语言。
-但 EVM 不理解可靠性或任何高级语言。它理解字节码，即一种低级语言。
-现在写字节码不是人类可读的，所以我们转换我们的 SOLIDITY - >字节码，然后发送到 EVM。
-但是我们也需要 ABI(应用二进制接口)。这有助于我们的 JavaScript 代码与 EVM 字节码进行交互。
-现在我们可以使用许多包将我们的智能合约转换成 ABI 和字节码。其中很少是“solcjs”、“ethers”、“hardhat”等等。

这是 EVM 处理智能合同的方式。在下一篇文章中，我们将会看到更多关于 ABI、字节码以及如何将智能合约转换成字节码的细节。我们还将学到稳健的基础知识，以及如何撰写明智的合同等等..

> **你好，我是 Tanisk Annpurna
> 我发布关于**
> 
> **🚀web3、区块链、以太坊**
> 
> **🐦智能合同，可靠性**
> 
> **🎉JavaScript，ReactJS，NodeJS
> 关注并喜欢更多这样的帖子。
> ！！✌️!！**