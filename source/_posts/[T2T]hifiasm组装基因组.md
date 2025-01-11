---
title: hifiasm基因组组装
date: 2025-01-11 11:21:37
categories: T2T组装教程
cover: /img/cover2.jpg
tags: 基因组组装
---

b站：[CGM第423期-程昊宇-基因组从头组装算法hifiasm](https://www.bilibili.com/video/BV1cx4y147x1/)

github:[Hifiasm: a haplotype-resolved assembler for accurate Hifi reads](https://github.com/chhylp123/hifiasm?tab=readme-ov-file)

说明文档:[Hifiasm](https://hifiasm.readthedocs.io/en/latest/#)

> publication:
>
> > Cheng, H., Concepcion, G.T., Feng, X., Zhang, H., Li H. (2021) Haplotype-resolved de novo assembly using phased assembly graphs with hifiasm. *Nat Methods*, **18**:170-175. https://doi.org/10.1038/s41592-020-01056-5
>
> > Cheng, H., Jarvis, E.D., Fedrigo, O., Koepfli, K.P., Urban, L., Gemmell, N.J., Li, H. (2022) Haplotype-resolved assembly of diploid genomes without parental data. *Nature Biotechnology*, **40**:1332–1335. https://doi.org/10.1038/s41587-022-01261-x
>
> > Cheng, H., Asri, M., Lucas, J., Koren, S., Li, H. (2024) Scalable telomere-to-telomere assembly for diploid and polyploid genomes with double graph. *Nat Methods*, **21**:967-970. https://doi.org/10.1038/s41592-024-02269-8

> 知乎参考：
>
> [用Hifiasm基于HiFi数据组装基因组：（一）简介Hifiasm软件和HiFi数据](https://zhuanlan.zhihu.com/p/704627156)









组装基因组的方式 

有参考基因组的

还有没有参考基因组的de nove组装

有参考基因组也会有缺陷

![](https://pic1.imgdb.cn/item/677fc3b4d0e0a243d4f2ca71.png)



- 测序数据
  - short
  - long

# hifisam pipeline

![](https://pic1.imgdb.cn/item/677fd8ddd0e0a243d4f2cf09.png)

从reads组装成contigs的传统流程会有一些问题

然后就开发了hifiasm





![](https://pic1.imgdb.cn/item/678204afd0e0a243d4f349e3.png)

hifiasm的组装效率也很高

# Motivation1

![](https://pic1.imgdb.cn/item/678204afd0e0a243d4f349e3.png)



- **问题**：传统组装方法（随机相位组装）无法准确区分父母本的变异信息，影响组装质量。

- **解决方案**：使用三体分组（Trio-binning），结合父母本信息进行单倍型解析组装。

- **局限性**：三体分组对父母本信息的依赖性可能限制其应用场景。



HiFiAsm 的设计目标是通过这种方法实现更高质量的基因组组装，同时探索如何应对父母本信息缺乏的情况。

![](https://pic1.imgdb.cn/item/67821407d0e0a243d4f35522.png)



Hi-C 的 **长距离信息** 是它解决基因组组装问题的关键。以下是具体原因和机制：

1.**解决单倍型（Haplotype）解析问题：**

- 在二倍体或多倍体基因组中，来自父本和母本的染色体序列高度相似，但又存在差异（变异位点），这使得组装过程难以准确区分父本和母本来源。

- Hi-C 的数据可以跨越多个变异位点（如图中红色和蓝色虚线），将同一单倍型上的变异点连接在一起，从而帮助解析父本和母本的单倍型。

2. **辅助长序列组装（Long-Read Assembly）：**

- 虽然长读取技术（如 PacBio 和 Nanopore）可以提供高达 15-30 kb 的长读段，但它们在 **更远距离的连接信息** 上仍然有局限。

- Hi-C 数据可以提供高达 **100 Mb** 的远距离相互作用信息，弥补了长读取技术在长距离组装上的不足。

![](https://pic1.imgdb.cn/item/6782156ed0e0a243d4f355a7.png)

1. **整体流程：从原始读取（Raw reads）到最终组装（Final assembly）**：

- **Raw reads（原始读取）：**
  - 通过高通量测序技术得到的原始测序数据。

- **Corrected reads（修正读取）：**
  - 对原始读取进行质量控制和校正，消除测序误差。

- **Phased assembly graph（相位组装图）：**
  - 通过 Hi-C 数据的相位信息构建组装图，标注节点的同源性和单倍型信息。

- **Final assembly（最终组装）：**
  - 结合 Hi-C 提供的长距离联系信息，将相位组装图解析为实际的线性序列（例如 contigs）。

2. **输入数据（Input）：**

   - **Heterozygous nodes（杂合节点，本地相位）：**表示存在变异的杂合区域，在相位组装中需要区分这些节点所属的单倍型。

   - **Hi-C links among nodes（Hi-C 节点连接，全局相位）：**
     - Hi-C 提供的长距离相互作用信息用于全局相位。
     - **作用**：将同一单倍型内的节点聚类（cluster nodes within the same haplotype）。

   - **Homologous pairs（同源配对节点，本地相位）：**
     - 标记同源区域，表明某些节点属于不同单倍型。
     - **作用**：将这些节点分配到不同的单倍型（separate nodes to different haplotypes）。

3. **Hi-C 相位（Hi-C phasing）：**

   - Hi-C 数据在这里起到了关键作用：

   - 通过 Hi-C 数据中跨越多个节点的长距离信息，将同一单倍型内的片段聚类在一起（例如图中橙色和蓝色的连接线）。

   - 在构建相位组装图的基础上，进一步优化全局的单倍型解析。

4. **输出数据（Output）：**

- **最终线性序列（例如 contigs）：**
  - HiFiAsm 利用 Hi-C 提供的节点联系信息，生成完整的线性组装序列。
  - 这些序列是按单倍型划分的，能够分别解析父本和母本的单倍型。

- **同源性区域（homology）：**
  - 图中展示了组装结果如何处理同源区域（黄色和蓝色块），通过 Hi-C 数据区分同源片段并进行正确连接。

![](https://pic1.imgdb.cn/item/678216d9d0e0a243d4f355ff.png)



将 **单倍型解析（phasing）问题** 转化为一个 **最大切割问题（max-cut problem）** 来解决



# Motivation2

![](https://pic1.imgdb.cn/item/67821aa2d0e0a243d4f357aa.png)

1. **标题：长且准确的读段仍然不足以解决复杂基因组**
   - 虽然长读段（如 PacBio HiFi）提供了高质量和更长的读取，但在一些基因组复杂区域，长度仍不足以解决这些问题，导致组装中断。

**2. 左侧图：现有组装方法的失败案例**

- **问题：SMN1/SMN2 基因的组装失败**：

  - **SMN1/SMN2 基因**：

  - 这是一个与 **脊髓性肌萎缩症（Spinal Muscular Atrophy，SMA）** 相关的基因。

  - 它位于一个高度复杂的基因组区域，具有高度同源性和重复序列。

- **现象：组装图中断（Breaks in the assembly graph）**：
  - 由于读取长度不足以跨越复杂区域，组装图（assembly graph）中出现多个断裂点，无法正确解析出完整的基因组序列。

- **HiFiAsm 的限制**：
  - 尽管 HiFiAsm 是一个高效的组装工具，但当遇到像 SMN1/SMN2 这样复杂的区域时，现有 HiFi 读段长度可能不足，组装会失败。

**3. 右侧图：使用更长读取的改进**

- **解决方法：使用更长的读段**：
  - 通过采用更长的读取（如 Ultra-long Nanopore Reads 或进一步改进的 PacBio 读段），能够跨越复杂区域并正确解析这些重要的基因组区域。
- **效果：更完整的组装图**：
  - 如图所示，使用更长的读段可以生成更加连贯的组装结果，完全覆盖复杂区域，解决组装图断裂的问题。

- **医学意义**：
  - 解析出完整的 **SMN1 和 SMN2 基因区域** 对于脊髓性肌萎缩症的研究和诊断具有重要意义。

**4. SMN1 基因和 SMA 的背景信息**

- **SMN1 基因**：

  - SMN1 基因编码一种生存运动神经元蛋白，负责神经元的正常功能。

  - 其突变会导致 **脊髓性肌萎缩症（SMA）**，这是一种影响神经肌肉功能的遗传性疾病。

- **SMN2 基因**：

  - 与 SMN1 基因高度同源，但功能性稍有不同。

  - SMN1 和 SMN2 的复杂性在于它们的高相似度和重复序列，使得基因组组装极具挑战。

![](https://pic1.imgdb.cn/item/67821cfbd0e0a243d4f3588f.png)

结合 **HiFi/duplex 读段**（高准确度）和 **超长读段（Ultra-long, UL reads）**（大覆盖长度）以解决复杂基因组区域问题的策略

**结合两种读段：**

- **目标**：利用 HiFi 读段的高准确性来校正 UL 读段的高错误率，同时利用 UL 读段的超长覆盖来补充 HiFi 读段在复杂区域中的不足。

- **策略**：
  - **HiFi reads 提供精确的碱基校正和本地解析**。
  - **UL reads 提供全局的长距离联系信息**，解决重复和复杂区域问题。
