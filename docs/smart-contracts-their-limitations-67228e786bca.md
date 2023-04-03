# 智能合同及其局限性

> 原文：<https://medium.com/coinmonks/smart-contracts-their-limitations-67228e786bca?source=collection_archive---------4----------------------->

![](img/7f9f6214ad9fcd2349cba2fc12aad683.png)

Smart Contract Limitation

近年来，区块链技术的使用呈爆炸式增长。推动区块链大规模采用的一项创新是**智能合约和以太坊虚拟机。**让我们深入了解一下什么是智能合约。

智能合约是通过对等网络分发和存储的代码，可以调用它来执行逻辑和存储信息。创造“智能合同”一词是因为其性质；它们是公开的、不可改变的、自我执行的、自我验证的，任何与契约交互的参与者都同意这些结果。

尽管智能合约的概念很古老，但直到以太坊的虚拟机，智能合约才像今天这样开花结果。

智能合约的引入彻底改变了区块链简单分类账之外的东西:衍生品、自动做市商、NFT、身份安全、GameFi 等等。

随着时间的推移，EVM(以太坊虚拟机)的改进分支得到了发展，但智能合约的核心功能相对保持不变。这对于跨各种链和网络的可组合性来说非常好，但是智能契约的局限性在整个 web 3 领域也是显而易见的。

# 智能合同限制

![](img/a313ac640d560bf4ec8a0e065e0588e5.png)

**弃用逻辑**

可以通过委托和库使用链上的现有逻辑，这意味着不必在链上重新部署现有逻辑。这是 EVM 的一个惊人的特性，并且降低了开发成本。然而，突破性的版本变更、不断变化的标准实现和 gas 效率的提高经常会导致旧库过时。因为不同的链通常不共享相同的状态，所以必须在参与者想要与之交互的每个链上部署逻辑。超过 60%的智能合约从未看到任何真正的用途。

**气体和尺寸限制**

理想情况下，随着时间的推移，越来越复杂的逻辑可以添加到链中，从而构建一个多样化的支持网络；然而，进展缓慢得令人失望。由于解决方案的庞大文件大小，一些逻辑也不适合存储在 chain 上。

这对于部署或上传契约的参与者来说都是一个问题，因为他们必须有效地为节点付费以永久存储代码；并且每当与合同交互时，因为更复杂的代码需要更多的操作码，这也增加了气体成本。天然气价格和连锁基础面值的成本使得将逻辑部署到区块链非常昂贵，并且对低层呼叫的依赖会受到连锁拥塞的极大影响。

**自动化**

智能合约的另一大局限是缺乏自主性:区块链上的所有事件都是由外部拥有的账户(EOA)触发的。契约可以与其他契约交互，但通常需要在它们的代码中显式集成逻辑，并且只有在 EOA 指示时才能这样做。

**数据**

最后，数据是智能合约的另一个限制。网络上的任何信息(如果公开的话)都是可靠且廉价的，但是所有其他数据只能由 EOA 引入，这带来了大量的安全问题。

请继续关注下一篇文章，在那里我们将了解各种协议如何处理这些问题并努力提供解决方案。

> 交易新手？试试[密码交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或者[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)