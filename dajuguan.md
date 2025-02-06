---
timezone: Asia/Shanghai
---


---

# Po

1. 自我介绍：`我是EthStorage的研究员, 主要研究ZK和Layer2欺诈证明等`
2. 你认为你会完成本次残酷学习吗？`Yes`

## Notes

<!-- Content_START -->

### 2025.02.06
Week 1: Protocol Intro

- 以太坊升级主要通过EIP提案 
- 执行层和共识层规范,采用python版本更容易理解
- The Merge升级之后包括执行层和共识层
    - 执行层: 
        - EVM执行交易;采用Merkle Patricia Trie存储账户、合约代码等状态数据,;执行层节点之间通讯采用JSON-RPC,;应用层采用JSON-RPC API与执行层交互
        - 有多个客户端实现: go_ethereum, reth
    - 共识层: 
        - LMD GHOST (Latest Message Driven - Greedy Heaviest Observed SubTree)作为fork choice rule, 它决定链的最新规范区块;共识层节点有另一个P2P网络来通讯;RANDAO
        - 有多个客户端: Prysm, lighthouse等

    - 执行层和共识层通过Engine API来通讯
- 社区讨论:
    - [Dev calls](https://t.co/uws1gxb4a0)
    - 论坛: @EthMagicians, @ethresearchbot
    - Discord: Ethereum R&D discord(https://discord.com/invite/qGpsxSA)
- [Week 1相关资料](https://github.com/IntensiveCoLearning/Ethereum-Protocol-Fellowship/issues/73)

### 2025.02.07

<!-- Content_END -->