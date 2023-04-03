# 证明区块链硬币的所有权

> 原文：<https://medium.com/coinmonks/proving-ownership-of-coins-in-blockchain-a69ad11c3eec?source=collection_archive---------28----------------------->

## 区块链

![](img/2da6ccf9e0fbccbcb4ef1ce510dc700b.png)

在上一篇文章中，我们开始讨论区块链交易，并了解了我们如何使用公钥创建区块链账户地址。在这篇文章中，我们将了解更多关于区块链账户地址，它们如何被用来证明比特币的所有权，以及区块链交易如何更详细地工作。

为了理解我们如何使用区块链账户地址来证明所有权，我们需要了解我们如何在交易中发送和接收比特币。

这里我们遇到了一个有趣的障碍。要了解账户如何接收比特币，我们需要了解账户如何发送比特币。要了解账户如何发送比特币，我们需要了解账户如何接收比特币。一个经典的[第二十二条军规](https://en.wikipedia.org/wiki/Catch-22_(logic))。

尽管如此，我们必须从某个地方开始。所以，我们先从研究我们如何向账户发送比特币开始，然后学习账户如何接收比特币。毕竟，一个事务的输出是另一个事务的输入，反之亦然，我们很快就会看到。

> 交易新手？在[最佳加密交易](/coinmonks/crypto-exchange-dd2f9d6f3769)上尝试[加密交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)

# 发送比特币

现在，我将使用我在上一篇文章中使用的同一个例子。我们有两块比特币——一块价值 0.75 比特币，另一块价值 0.4 比特币。暂且假设这些是属于我们的，不需要证明所有权。稍后，我们可以看到帐户如何接收比特币并证明所有权。

区块链交易只是输入和输出的集合。他们的工作方式就像我们上一篇文章中的黄金经纪人一样。我们输入比特币，并指定我们想把钱输出给谁。我们已经有了自己的输入，所以让我们看看如何将钱输出到书店。

在我们开始交易之前，我们需要知道书店的区块链地址。我们可以通过应用程序或地址字符串来解码 QR 码。无论哪种方式，这个地址，如前所述，将是一个字节 58 编码的字符串。

为了把钱送到书店，我们需要找到他们的公钥散列。这被编码在地址串中。一旦我们解码了地址，我们将得到公钥散列以及地址版本和校验和。

# 公钥脚本

然后，我们可以使用 pubkey 散列来创建 pubkey 脚本。这个 pubkey 脚本包含 pubkey 散列和一些将用于验证事务的脚本。pubkey 散列告诉我们要将事务输出给谁。pubkey 脚本中的脚本将允许该交易的接收者在将来证明他们的所有权。稍后我们将了解更多这方面的内容。

因为我们想把钱寄给书店，所以我们将使用书店的 pubkey 散列来创建 pubkey 脚本。既然我们已经提到了我们要把钱寄给谁，现在是我们提到金额的时候了。但是记住，我们只需要付给他们 1 个比特币，但是我们已经输入了 1.15 个比特币。把剩下的 0.15 比特币寄回我们的账户就能拿回来。因此，我们可以用我们帐户的公钥散列创建另一个公钥脚本，并指定金额。如您所见，我们实际上可以在单个事务中有许多输出。

现在我们已经建立了一个事务。太好了，现在我们可以执行交易了，不是吗？但是等等。还记得我们刚刚假设输入的比特币是属于我们的吗？要执行这项交易，我们需要证明它们确实属于我们。

正如我们前面讨论的，要能够花钱，你应该已经收到了钱。换句话说，为了将比特币输入到交易中，我们应该已经从其他一些交易中收到了这些比特币，作为发送到我们帐户的输出。

# 接收比特币

考虑将接收我们的事务输出的书店。他们可以将产出的比特币作为新交易的投入来消费。类似地，为了能够执行交易，我们应该已经接收到比特币作为先前交易的输出。正如我们之前假设的，我们的账户有价值 0.75 比特币和 0.4 比特币的输出。我们一定是在前两次交易中收到的。但是我们如何证明这些输出是属于我们的呢？

让我们看看如何在尚未完成的交易中向书店输出比特币。我们有两个不同的输出，每个输出都有一个包含接收者的公钥散列和金额的公钥脚本。把我们的比特币输出到我们账户的交易也应该有类似的信息。我们可以通过参考这些交易来证明我们拥有这些比特币。但是我们如何引用这些交易呢？

# 交易 ID

每个事务——它的输入和输出——都可以被散列以产生唯一的字符串。区块链对交易进行两次哈希处理，以确保更好的安全性。也就是说，事务被散列，并且产生的散列被再次散列。这个散列用作事务 ID (TXID)。我们可以通过在新事务的输入部分提到 TXID 来引用事务。但是，一个事务可以有几个输出。所以，我们还需要提到属于我们的产出指标。

假设书店决定花掉我们寄给他们的比特币。他们可以通过提及我们发起的交易的 ID 和他们输出的指数来引用他们的比特币。我们的交易还通过使用我们的地址将剩余的 0.15 比特币发回给我们。我们可以通过引用事务 ID 和输出索引在新事务中使用它们。

# 证明所有权

现在我们已经参考了交易和相关输出，可以证明输出的比特币是属于我们的。事务输出中的 pubkey 脚本有一个 pubkey 散列，它是我们的公钥的散列。我们有对应于那个公钥的私钥。使用私钥，我们应该能够证明输出属于我们，但是我们如何做到这一点呢？

# 数字签名

帮助我们的是我们之前学过的数字签名。我们可以使用交易的数字签名来证明所有权。为了生成交易的数字签名，我们可以对交易(它的输入和输出)进行两次哈希运算，然后用我们的私钥对它进行加密以生成数字签名。

然后，我们使用这个数字签名来创建签名脚本，我们将把它附加到交易中。签名脚本包含交易的数字签名和我们的公钥。

为了验证所有权，我们可以使用签名脚本中的公钥解密签名。因为只有使用我的私钥生成的签名才能被我的公钥解密，所以这证明我签署了该事务。我可以将公钥散列两次，并显示它与我在当前交易中用作输入的先前交易的输出的 pubkey 脚本中的 pubkey 散列相同，以显示我拥有这些比特币。

因此，我们不仅证明了比特币属于我们，还证明了我就是我所声称的那个人，而且是我把我的钱送到了书店。

我们现在已经看到了如何证明比特币的所有权。我们也看到了所有权是如何被肤浅地核实的。在下一篇文章中，让我们更详细地看看如何验证事务。

*原载于 2022 年 11 月 20 日*[*【https://www.thearmchaircritic.org】*](https://www.thearmchaircritic.org/mansplainings/proving-ownership-of-coins-in-blockchain)*。*