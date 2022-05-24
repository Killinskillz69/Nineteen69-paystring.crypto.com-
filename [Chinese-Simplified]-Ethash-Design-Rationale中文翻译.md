<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

:stop_sign: This wiki has now been deprecated. Please visit [ethereum.org](https://ethereum.org/zh) for up-to-date information on Ethereum. :stop_sign: 

**Contents**

- [FNV](#fnv)
- [参数](#%E5%8F%82%E6%95%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Ethash旨在满足以下目标：

1. **IO饱和度**: 该算法应该消耗几乎所有可用的内存访问带宽（这是实现抗ASIC的策略，其论点是商品RAM，尤其是GPU中的商品RAM，比商品计算容量更接近理论最优）
2. **GPU友好性**: 我们尝试尽可能简单地使用GPU进行挖矿。以CPU作为目标几乎肯定是不可能的，因为潜在的专业化收益太大，并且存在对CPU友好算法的批评，它们容易受到僵尸网络的攻击，因此我们将GPU作为折衷方案。
3. **轻客户端可验证性**: 轻客户端应该能够在C语言的桌面台式机上在0.01秒内验证一轮挖矿，在Python或Javascript中验证不到0.1秒，最多消耗1 MB内存（但指数增加）
4. **轻客户端减速**: 在轻客户端上运行算法的过程应该比使用完整客户端的过程慢得多，以至于轻客户端算法不是经济上可行的实现挖矿实现的途径，包括通过专用硬件。
5. **轻客户端快速启动**: 轻客户端应该能够完全运行并能够在40秒内在Javascript中验证区块。

### FNV

FNV用于提供数据聚合功能，其是（i）非关联的，以及（ii）易于计算。 FNV的一个交换和联合替代方案将是异或。

### 参数

* 选择16 MB缓存是因为较小的高速缓存允许使用光评估（light-evaluation）方法太容易地生成ASIC。 16 MB缓存仍然需要非常高的缓存读取带宽，而较小的高速缓存可以更容易地被优化。较大的缓存会导致算法太难而不能使用轻客户端进行评估。
* 每个DAG项选择256个父项，以确保时间 - 内存权衡（折衷）只能以低于1：1的比例进行。
* 选择1 GB DAG大小是为了要求内存级别大于构建大多数专用内存和缓存的大小，但仍然足够小，以便普通计算机能够使用它。
* 每年约0.73倍的增长水平被选择为大致与摩尔定律至少在最初的增长平衡（指数增长有超过摩尔定律的风险，导致挖矿需要非常大量的内存而普通的GPU不再能用于挖矿）。
* 64次访问被选择是因为大量访问会导致轻验证耗时太长，而较小的数量意味着大部分时间消耗最终是SHA3，而不是内存读取，这使得算法不具备强IO约束。
* 时期（epoch）长度不能是无限的（即，常量数据集），因为那时算法可以通过ROM优化，并且非常长的时期（epoch）长度使得更容易创建被设计为非常不频繁地更新并且仅经常读取的内存。过短的时期（epoch）会增加进入壁垒，因为弱机器需要花费大量时间在更新数据集的固定成本上。如果设计需要的话，可以大大减少或增加时期（epoch）长度。
* 缓存大小和数据集大小是素数，是为了帮助减轻数据集项在生成或挖矿中出现的循环风险。