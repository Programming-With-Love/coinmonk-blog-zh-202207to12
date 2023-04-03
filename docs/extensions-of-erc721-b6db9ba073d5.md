# ERC721 的扩展

> 原文：<https://medium.com/coinmonks/extensions-of-erc721-b6db9ba073d5?source=collection_archive---------13----------------------->

在我之前的文章[中，我描述了最常用的令牌标准——ERC 20 的扩展。现在是第二流行的令牌标准——ERC 721 的时候了。所有扩展都来自 OpenZeppelin 库。](/coinmonks/extensions-of-erc20-521b7891e39)

![](img/20cc7ff1c4b65fb583744759705f56ce.png)

# 核心接口

主要的也是唯一必须的接口是 ERC721，它是 ERC721 标准最简单的实现。除此之外，还有两个核心实现:ERC721Metadata 和 ERC721Enumerable。对于最重要的接口，我们还可以数 IERC721Receiver，这与我提到的其他接口不同。

## ERC 721 元数据

这个接口允许我们向令牌添加名称和符号。此外，它实现了一个公共函数`tokenURI`，该函数连接了基本 Uri 和`tokenId`。所以我们可以附加一些外链信息到我们的 NFT。

## ERC 721 可数

每枚铸造的代币都有自己独特的 uint256 `tokenId`。最频繁的，`tokenId`从零开始递增，很容易发现哪个令牌比较老。但这不是规则。`tokenId`可以通过完全随机的机制来设置。因此，此接口从所有令牌 id 列表中创建，这些令牌 id 只是从零开始增加。此外，除了为所有令牌创建一个列表之外，还为每个令牌所有者创建了一个列表。这个解决方案使用户的生活更容易。

## ERC721Full

连接到 ERC721、ERC721Metadata 和 ERC721Enumerable 的接口。由该工具创建的令牌是全功能令牌。

## ierc 721 接收器

必须由想要支持 ERC721 的`safeTransfer`功能的契约实现的接口。通过使用`safeTransfer`,我们最大限度地降低了令牌在任何智能合约中被永远锁定的风险。它是如何工作的？如果`safeTransfer`的目标是契约，函数将调用`IERC721Receiver.onERC721Received`，被调用的函数必须返回值等于`bytes4(keccak256(“onERC721Received(address,address,uint256,bytes)”))`。否则，交易将被恢复。通过使用此解决方案，我们不会向不是为处理 ERC721 而创建的契约发送令牌。

# 扩展ˌ扩张

除了主接口，OpenZeppelin 库还为我们提供了额外的特性契约，扩展了普通的 ERC721。

## ERC 721 可燃

这个扩展的名字就是线索，它做了什么—燃烧令牌。更准确地说，如果我们实现这个扩展，我们将能够不可逆地销毁一个特定的令牌。这个函数是公共的，名为`burn`。使用它的唯一要求是`msg.sender`必须是他想要刻录的令牌的所有者，或者他必须获得此合同的批准。

## ERC 721 连续

这种扩展允许铸造大量令牌，但仅在合同构建期间。默认情况下，批量的上限是 5000 个令牌。当生成批处理时，IERC721Receiver 实现的方面不会检查拥有这些令牌的帐户的地址。除此之外，这个扩展还改变了一件事——在构造函数中，我们不能使用传统的函数`mint`来创建单个令牌。只有当构造函数被完全执行时，我们才能使用这个函数。

## ERC 721 暂停

该扩展实现了标准 ERC721 契约的紧急停止机制，该机制可以由授权地址触发。它是通过增加两个新的修饰符:`whenNotPaused`、`whenPaused`和修改 ERC721 的`_beforTokenTransfer`函数而制成的。这一修改暂停了`_transfer`、`_mint`和`_burn`的工作。

当我们希望在评估过程中停止所有令牌传输，或者在代码中发现严重错误时，此扩展非常有用。这只是一个出现的红色大按钮，暂停一切工作。

## ERC 721 可靠性

执行 ERC2981 (NFT 版税标准)。当 NFT 被出售时，每卖出一件作品，创作者都会得到售价的一定百分比——这个百分比被称为版税。不幸的是，每个市场都有自己的版税系统，因此，当 NFT 在不同的市场出售时，创作者收不到钱。为了使 NFT 的这一方面标准化，创建了 ERC2981。这个 ERC 指定了一种用信号表示版税信息的方式。但它只是如何保存这些信息的标准，所以它不会强制市场支付。因此，市场有望在销售的同时自愿支付版税。目前，这种扩展不是很受欢迎，而且市场经常不想支付版税。

## ERC 721 uri 存储

正如在 ERC721Metadata 段落中所说，我们可以将字符串变量添加到特定的令牌中。但是这个字符串总是由基本的 URI 和`tokenId`连接而成。此解决方案非常高效，因为每个令牌的 URI 不必是链上存储。但问题是，当我们想要添加的 URI 不与`tokenId`连接时，或者当不同的令牌需要不同的基本 URI 时。为了解决这个问题，我们可以使用这个扩展。它允许我们在链上存储特定的 URI。

## ERC 721 投票

该扩展感谢我们可以使用 ERC721 进行投票，并创建自己的治理系统的元素之一。一个代币等于一个投票单位。这个扩展支持投票和委托某人投票。这一扩展的重要方面是，令牌在被委托之前不能算作投票，因为投票必须被跟踪。这是一个非常流行的限制，我们可以在 [ERC20Votes 扩展](/coinmonks/extensions-of-erc20-521b7891e39)中找到。

# 附加常用接口

我在这篇文章中提到的许多智能合约都使用一个合约— ERC165。因此，我认为我们应该拥有一些关于它的信息，即使它不是 ERC721 扩展。在我的研究中，我发现了一个关于 ERC165 的很棒的帖子，我肯定不会更好地解释它，所以[这里是链接](/@chiqing/ethereum-standard-erc165-explained-63b54ca0d273)。我觉得真的很值得一读。

我希望这篇文章对你有用。如果你有任何想法，我如何能使我的帖子更好，请告诉我。我随时准备学习。你可以在 [LinkedIn](https://pl.linkedin.com/in/szymon-skrzy%C5%84ski-881462214) 和 [Telegram](https://t.me/eszymi) 上和我联系。

如果你想和我谈论这个话题或者我写的其他话题，请随意。我乐于交谈。

快乐学习！

> 交易新手？尝试[加密交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)