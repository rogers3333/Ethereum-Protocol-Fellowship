---
timezone: Pacific/Auckland
---

# Bruce Xu

1. 自我介绍：大家好，我是 Bruce Xu，以太坊爱好者，LXDAO 和 ETHPanda 联合发起人，很开心参加今年的 EPF 残酷共学。
2. 你认为你会完成本次残酷学习吗？会的！

## Notes

<!-- Content_START -->

# 2025.02.06

今天先把 https://epf.wiki/#/ 大概得过一下，看看整体结构和一些相关的信息，列一些 TODO 记录自己感兴趣的话题和内容，进行下一步的学习。

填写了 survey：<https://forms.gle/G5V95qyGV8uMjKGcA>

今年的 EPFsg 是 2 周 intense 的之前课程回顾，然后 6 周新的在线课程，覆盖几个部分。

TODO 这两周可以快速复习 https://epf.wiki/#/eps/SG2024 24 年的课程和笔记。


## [Prehistory of Ethereum](https://epf.wiki/#/wiki/protocol/prehistory)

以太坊的愿景来自于互联网早期的开放精神、Unix、GNU/Linux、Cypherpunks、比特币等等，构建一个无边界、自我主权的数字经济生态。

"National borders are just speed bumps on the information superhighway."
— Timothy May, Cypherpunk.

互联网的兴起，打破了国家的便捷，促进了不可想象的人类互动。

密码学和开源软件作为根基，促进了互联网新人，助推了电子商务和网上银行业务的增长。

Free software 的 free 是 freedom 而不是 price。但是 FOSS 是非常有价值和贡献的。

90 年代开始，密码朋克就有很多次对于实现 digital currency 的尝试，例如 Digicash、E-Gold、B-Money、Bitgold、Bitcoin。而 Bitcoin 上面开发应用程序的几次尝试都失败了，所以有了 Ethereum 的诞生。

分享：<https://x.com/brucexu_eth/status/1887257222436298803>

## [Protocol Architecture Overview](https://epf.wiki/#/wiki/protocol/architecture)

执行层处理实际交易和用户交互，共识层提供证明的共识机制。

## [Protocol Design Philosophy](https://epf.wiki/#/wiki/protocol/design-rationale)

- 简单
- 普遍：图灵完备的虚拟机
- 模块化
- 中立不歧视
- 敏捷

原则：

- 尽量简单
- Freedom：使用时，不会受到限制或者歧视。
- Generalization
- 没有任何特性：可以通过智能合约自己设计

实际上我感觉以太坊协议还是太复杂了，避免不了软件工程的屎山的归途。按照架构的演进，模块化肯定是必然，分层的设计需要非常清晰和能看到全局的资深研究员。

TODO 绘制以太坊的分层架构图。

UTXO vs Account：这是个比较大的话题，不过智能合约的实现，账号确实是比较好的选择。

Merkle-Patricia Trie 是以太坊的存储数据结构，高效检索的能力构成了以太坊状态的各项数据。

TODO 获取一下以太坊的 state tree 真实数据看看

MPT 正在被考虑弃用，准备使用 Verkle tree，实现更高效的数据结构。

TODO 简单了解 MPT 之后，重点研究 Verkle tree

目前的节点状态数据包括 1-2TB，其实挺麻烦的，启动节点等还是比较麻烦的。

# 2024.02.07

## [Protocol Design Philosophy](https://epf.wiki/#/wiki/protocol/design-rationale)

Recursive Length Prefix (RLP) 创建新序列化方案的理由在于其他方案的概率性质。RLP 通过简单而确定的序列化解决了这一问题，并保证了绝对的字节级一致性。这是一个序列化数据的算法？

Simple serialize (SSZ) 序列化是将数据结构转换为可以传输并在以后重建的格式的过程。SSZ 是以太坊 2.0 信标链中使用的一种序列化格式。根据 Vitalik 的评论，SSZ 试图解决的一个主要问题是 RLP 不允许 Merkle 化，这将意味着排除了任何简洁轻客户端证明的可能性。因此，无法实现无状态性——而无状态性仍然是当前以太坊研发的关键目标。

Casper Friendly Finality Gadget (FFG) 用于实现 finality，finality 表示的是一个 block 和里面的数据，再也无法被修改或者 remove。通过在 proposal 机制之上，通过选择代表 canonical transaction ledger 的唯一链来最终确定区块。

Byzantine Fault Tolerance (BFT) 拜占庭将军容错是一个分布式计算系统的特性。应对的挑战是在一个去中心化的环境，如何在某些节点故障或者存在恶意行为下达成一致。比如 PoS 就是针对这个问题实现的算法，来确保在去中心化环境下实现一致。

Latest Message Driven Greediest Heaviest Observed Sub-Tree (LMD-GHOST) 是一个分支选择的规则。有点类似 PoW 使用的分叉选择，其中完成最多工作的被选为 canonical chain。

Gasper 是一个完全的 PoS protocl，结合了 casper FFG 和 LMD-GHOST 来推动 Eth2 的共识层机制。

Using a DHT DHT（分布式哈希表）的主要优势在于，它的查找操作在网络中仅产生对数级别的通信开销。因此，它非常适用于在 P2P 网络中查找（查询）内容。但一个直接的问题是：在以太坊中，我们为什么需要查找内容？毕竟，大多数节点都关注相同的内容——即最新的区块。由于共识槽（consensus slot）在每个时刻只会产生一个区块，并且该区块通过gossip 协议进行传播，因此链的最新状态（tip of the chain）始终是一致的。在 BitTorrent 和 IPFS 这样的协议中，DHT 用于存储各种内容，并帮助用户查找他们感兴趣的内容。而在以太坊的网络层，DHT 并不是用于查找区块，而是用于发现不同的对等节点（peers）。

discv5 是一个 Ethereum 使用的 discovery protocol，使用 kademlia based DHT 来存储 ENR records. ENR 记录包括路由信息来建立 P2P 链接。




<!-- Content_END -->
