# CSC 101-气体优化第 2 部分

> 原文：<https://medium.com/coinmonks/csc101-gas-optimization-part2-2c4ba80a8de9?source=collection_archive---------26----------------------->

智能合同天然气优化是智能合同开发的最重要部分之一。这对我们减少能源消耗很有帮助。

为了成功，我们需要学习稳健如何处理我们的变量和功能。在本教程中，我们想谈谈坚固性优化方法。

这篇文章将为你提供一些在智能合同中减少汽油消耗的技巧。

![](img/78db353f85d00a7149d8bc2b6bc3c9de.png)

也许你有使用其他编程语言的经验，但是当你在像区块链这样的分布式系统上运行程序时，你必须用不同的方式思考问题。

Solidity 是一种编译语言，其中每个操作都被转换成 EVM 可以理解和解释的低级 opco。然后，你在程序中写的每一个操作都会在网络中的每一台计算机上执行，这就是为什么每一个操作都要花费“汽油”来防止垃圾邮件，更重要的是，防止无限循环。在可靠性方面，了解机器可读操作和它们的相关成本确实可以为你省钱。

## 功能名称

Solidity 编译器通过选择器读取和执行函数名。函数的选择器由函数签名(函数名和参数类型)的 keccak256 散列的前四个字节组成。例如:

```
function MyFunction(uint256 _value, string[] memory _names) external {}
```

在这种情况下:

*   函数 signature = "tryThis(uint256，string[])"
*   功能选择器= keccak256(签名)= 0x7f6ca090。

Solidity 编译器将通过选择器(以十六进制顺序)对契约中的所有函数进行排序，并在执行任何函数调用时检查每个函数，以检查哪个是被调用的函数选择器。履行合同上的每一项功能都要花费 22 美元。

## 冷访问与热访问

第一次访问一个变量要花 2100 气，第二次访问还要再花 100 气。这种气体成本的差异可能会变成一个大问题，特别是在循环遍历一个包含大量项目的动态大小的数组时。

在 Solidity 中缓存函数内部的数据可以降低能耗，即使这需要更多的代码行。在这个简单的例子中，缓存数据时节省了将近 2000 加仑汽油。

## 零值与非零值和汽油退款

在以太坊(总部位于 EVM)区块链上把一个值从 0 改成非零是很贵的(G*sset*= 20000 气)，而把一个值从非零改成 0，可以给你气值退款(转化为执行价格的折扣)。值得注意的是，一个人最多只能获得总交易成本的 20%的退款，这意味着只有在交易成本至少为 24，000 汽油的情况下，一个人才能获得退款。

## 内存与呼叫数据

将信息存储在 calldata 中总是比存储在内存中成本低，但它有一个明显的缺点。当使用 calldata 时，存储在其中的值不能在函数执行期间发生变化。因此，如果您需要在执行函数调用时更改变量的数据，请使用内存位置。如果您只需要读取数据，可以通过将数据存储在 calldata 中来节省一些时间。

> 交易新手？试试[加密交易机器人](/coinmonks/crypto-trading-bot-c2ffce8acb2a)或者[复制交易](/coinmonks/top-10-crypto-copy-trading-platforms-for-beginners-d0c37c7d698c)