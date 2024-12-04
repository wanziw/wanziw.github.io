---
title: 杨梅T2T论文阅读
date: 2024-12-04 10:36:21
categories: 论文阅读
cover: /img/cover10.jpg
tags: 
  - T2T
  - GWAS
description: "Horticulture Research杨梅的T2T组装和GWAS分析"
---

# 杨梅

[论文链接](https://academic.oup.com/hr/article/11/3/uhae033/7593780#443677756)

发表在《Horticulture Research》上

# Abstract 

这篇文章研究了中国杨梅（Myrica rubra或Morella rubra）的基因组及其与果实质量性状相关的遗传变异。具体工作包括：

​	1.**基因组组装**：使用PacBio HiFi长读技术，为‘枣佳’品种组装了一个端粒到端粒（T2T）的无间隙参考基因组，大小为292.60 Mb，揭示了8个着丝粒区域、15个端粒和28,345个基因。这显著提升了中国杨梅基因组的连续性和完整性。

​	2.**基因型重测序**：对173个样本进行重测序，鉴定出6,649,674个单核苷酸多态性（SNP）。

​	3.**表型分析与全基因组关联研究（GWAS）**：分析了29个与果实质量相关的表型性状，进行了GWAS，发现1937个SNP和1039个基因与28个性状显著相关。

​	4.**果色相关基因的发现**：在第6染色体的3407532至5153151 bp区域内发现了一个与果实颜色相关的SNP群，该区域包含两个MYB基因（MrChr6G07650和MrChr6G07660），在不同表型的转录组中表现出差异表达，关联于花青素合成。邻近的MrChr6G07670基因（MLP样蛋白）含有一个外显子错义变异，证明其能使烟草叶片中的花青素产量增加十倍。

​	5.**功能验证与应用**：该SNP群可能作为一个数量性状基因座（QTL），共同调控杨梅果实颜色。研究最终提供了完整的参考基因组，揭示了与果实质量相关的一系列等位变异，并鉴定了可用于提升杨梅果实质量和育种效率的功能基因。

# Introduction

> **Myrica L.** 属包括大约55种植物
>
> 中国杨梅（Myrica rubra）、木薯（Manihot esculenta）、矮杨梅（Myrica nana）、腺花杨梅（Myrica adenophora）、蜡杨梅（Myrica cerifera）、火山杨梅（Myrica faya）和里瓦斯杨梅（Myrica rivas-martinezii）

ZW染色体

> GWAS 在位点检测和精确基因定位方面具有很高的效率。然而，迄今为止，尚未对可用的 *M. rubra* 种质资源进行大规模的重新测序。对其他具有重要经济意义的作物（如番茄、葡萄和枇杷）的类似GWAS有助于鉴定**与果实颜色、大小、果肉质地、风味和营养/生物活性化合物**含量相关的特定基因和突变
>
> - 果实质量：多基因形状
>   - 果实质量由多种参数决定，包括外观质量性状（如形状、大小、颜色）和内在质量性状（如糖分、酸度和氨基酸水平）。
>   - 寻找创新育种的靶基因

- 依旧是讲了一下需要一个完整组装作为参考基因组的重要性，以此说明自己T2T组装的重要性

- 还是常规的展示了一下circos图、Hi-C的染色体交互图，还有 K-mer 分布 （17-mer） 光谱展示基因组大小

![](https://pic.imgdb.cn/item/674f058ad0e0a243d4dcdb03.png)

目前GWAS研究已经在西红柿、葡萄和枇杷等经济重要作物中发挥了重要作用，帮助识别与果色、果大、果肉质地、风味及营养/生物活性化合物含量相关的特定基因和突变。还没有在杨梅M. rubra种质资源进行，还没有大规模的重测序过

- 167 cultivated germplasm resources and six interspecific resources.
  - 167个不同的栽培品种/品系
  - 6个物种间资源（不同物种杂交）



# Results

## Assembly of a highly contiguous genome of *M. Rubra*

- 给了一个表介绍了一下T2T的组装

  - K-mer 分析估计 *M. rubra* 基因组大小为 282.20 Mb，杂合率为 0.85%

  - 最终产生了 292.60 Mb 的基因组组装，其重叠群 N50 大小为 36.50 Mb

  - （BUSCO） 数据库评估组装的完整性

- 8个着丝粒区域、7个碱基端粒重复序列鉴定15个端粒
  - 长末端重复 （LTR） 组装指数 （LAI）
- 预测注释了28 345 genes and 33 502 mRNAs
  - Repeat sequences：串联重复序列、穿插重复序列和转座因子 （TE）占43.43%。有助于鉴定，
  - T2T的一个优势就是长读长鉴定重复序列的，所以这里提了
- 和原本参考基因组的比较，优势巴拉巴拉
- 系统发育树
  - 植物间的进化关系，涵盖了**水果作物**（如苹果、杨梅、猕猴桃）、**坚果作物**（如核桃）、**粮食作物**（如水稻）以及**木本植物**（如木麻黄和单蕊花）
  - 基于**蛋白质同源物**（protein homologs）和**基因家族扩展与收缩**（gene family expansions and contractions）来构建的
    - **OrthoFinder** 用于识别不同物种之间的**同源基因**（orthogroups，OGs）。同源基因是指从共同祖先基因衍生出来的基因
    - 在**Myrica rubra（杨梅）\**中，有1014个基因家族扩展，4258个基因家族收缩。这些变化与\**叶绿体发育、果实成熟、抗逆性功能**等相关。
    - 杨梅与其他植物（如胡桃 Juglans regia）的分歧时间为6600万年

## Population structure analyses

种群结构分析

通过测了173个品种、与T2T比对，鉴定六百多万个SNP

使用KASP（一种湿实验）进行了一下验证

![](https://pic.imgdb.cn/item/674f21fbd0e0a243d4dce10e.png)

- 使用PCA把这些品种分为6组
  - 根据PCA的结果进行了详细的分析





这里系统发育树展示了173个品种之间的发育树，但是没写怎么来的，我思考了一下[使用SNPhylo基于SNP构建群体系统发育树](https://taoyan.netlify.app/post/2020-07-15.%E4%BD%BF%E7%94%A8snphylo%E5%9F%BA%E4%BA%8Esnp%E6%9E%84%E5%BB%BA%E7%BE%A4%E4%BD%93%E7%B3%BB%E7%BB%9F%E5%8F%91%E8%82%B2%E6%A0%91/)

（我猜的）可能是通过SNP数据来做的，可以达到全基因组水平，另外通过了一些方法比如连锁不平衡减少了SNP的冗余

也有可能是根据上面同源家族来做的

![](https://pic.imgdb.cn/item/674ee719d0e0a243d4dcc57c.png)



















`