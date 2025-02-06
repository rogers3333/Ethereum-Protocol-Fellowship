---
timezone: Asia/Shanghai
---

> 请在上边的 timezone 添加你的当地时区，这会有助于你的打卡状态的自动化更新，如果没有添加，默认为北京时间 UTC+8 时区
> 时区请参考以下列表，请移除 # 以后的内容

timezone: Pacific/Honolulu # 夏威夷-阿留申标准时间 (UTC-10)

timezone: America/Anchorage # 阿拉斯加标准时间 (UTC-9)

timezone: America/Los_Angeles # 太平洋标准时间 (UTC-8)

timezone: America/Denver # 山地标准时间 (UTC-7)

timezone: America/Chicago # 中部标准时间 (UTC-6)

timezone: America/New_York # 东部标准时间 (UTC-5)

timezone: America/Halifax # 大西洋标准时间 (UTC-4)

timezone: America/St_Johns # 纽芬兰标准时间 (UTC-3:30)

timezone: America/Sao_Paulo # 巴西利亚时间 (UTC-3)

timezone: Atlantic/Azores # 亚速尔群岛时间 (UTC-1)

timezone: Europe/London # 格林威治标准时间 (UTC+0)

timezone: Europe/Berlin # 中欧标准时间 (UTC+1)

timezone: Europe/Helsinki # 东欧标准时间 (UTC+2)

timezone: Europe/Moscow # 莫斯科标准时间 (UTC+3)

timezone: Asia/Dubai # 海湾标准时间 (UTC+4)

timezone: Asia/Kolkata # 印度标准时间 (UTC+5:30)

timezone: Asia/Dhaka # 孟加拉国标准时间 (UTC+6)

timezone: Asia/Bangkok # 中南半岛时间 (UTC+7)

timezone: Asia/Shanghai # 中国标准时间 (UTC+8)

timezone: Asia/Tokyo # 日本标准时间 (UTC+9)

timezone: Australia/Sydney # 澳大利亚东部标准时间 (UTC+10)

timezone: Pacific/Auckland # 新西兰标准时间 (UTC+12)

---

# KieSun

1. 自我介绍

    Web3 从业近三年，全栈工程师。

2. 你认为你会完成本次残酷学习吗？

    会！

## Notes

<!-- Content_START -->

### 2025.02.06

今天阅读了 [el-specs](https://epf.wiki/#/wiki/EL/el-specs)。其中设计到了大量的数学公式，所以结合 AI 帮助阅读。

大致整理了一个大纲：

```
让我为您总结这份关于以太坊执行层(EL)规范的文档:

# 主要主题
1. 执行层状态转换函数(STF)
2. 区块头验证
3. 交易执行流程
4. Gas定价和经济模型
5. Blob Gas机制

# 核心要点

## 状态转换功能
- 执行层专注于执行状态转换函数(STF),主要解决两个问题:
  - 区块是否可以添加到区块链末尾
  - 状态如何变化 [1]

## 区块验证流程
- 包括区块头验证、Gas使用验证、父区块验证等多个步骤
- 验证过程确保每个区块符合以太坊协议规则 [3]

## 交易执行机制
- 交易执行分为多个阶段:
  - 初始化检查点状态
  - 交易规范化和子状态初始化
  - 主执行阶段
  - 临时状态、预终态和最终状态的处理 [19][20]

## Gas经济模型
- 采用EIP-1559定义的动态基础费用机制
- 包含目标Gas限制、基础费用调整等机制
- 旨在提高网络效率和费用可预测性 [5][7]

## Blob Gas创新
- 引入了新的Blob交易类型
- 使用动态定价机制调节Blob Gas价格
- 设定了目标Blob Gas(~400KB)和最大限制(~800KB) [12][13]

# 技术亮点
1. 采用自然数作为区块参数,简化了计算和验证流程 [7]
2. 引入了访问列表(Access List)机制优化状态访问成本 [14]
3. 实现了可预测的基础费用调整机制 [5]
4. 集成了Blob交易支持,增强了Layer 2扩展性 [12]

# 重要更新
- 更新了状态转换函数的实现
- 优化了Gas计算模型
- 增加了Blob交易支持
- 改进了区块验证机制 [1][3][12]

这份规范文档详细定义了以太坊执行层的核心机制,为客户端实现提供了明确的技术指导。
```

对于其中 Blob 的内容需要学习下，明天整理一波内容。

<!-- Content_END -->
