
---
title: Sctail论文阅读
date: 2024-09-12 8:44:50
cover: https://pic.imgdb.cn/item/66e23a66d9c307b7e9112143.png
categories: 论文阅读
tags: PAS
description: PAS识别工具sctail
Copyright: true
copyright_author: wanzi
copyright_author_href: https://github.com/wanziw
copyright_url: https://wanziw.github.io/2024/09/12/%5B论文阅读%5DSctail论文阅读/
copyright_info: 此文章版權歸wanzi所有，如有轉載，請註明來自原作者
---
这篇文章有点乱搞，不看了


论文链接:[c](https://www.biorxiv.org/content/10.1101/2024.07.05.602174v1.full.pdf)
# Sctail

- 使用read1 5‘端测序，来识别PAS
- 然后使用read2 3’端来量化表达量
- APA
  - 单个基因选择的PAS位点，就是添加polyA的位点可以不同
- 目前的识别PAS的方法
  - 实验直接测得，所谓的PAS-seq
    - PolyA-seq、PAS-seq、3’READS和QuantSeq REV
  - 通过单细胞RNA-seq，再结合生物信息分析得到
    - scAPA、Sierra、scDaPars、MAAPER、scAPAtrap、SCAPTURE、SCAPE和Infernape



# Introduction





- （A） flow chart of the 3’ scRNA-seq gene expression library construction (10x Genomics).、
- （B）直方图显示了每个转录本的reads 1 5‘端和reads 2 3’端的末端到注释的PAS的最常见距离。

![](https://pic.imgdb.cn/item/66e23ca4d9c307b7e912ffa8.png)

- 这里有点看不懂
  - IGV的截图显示了正向链基因S100A9的reads 1、reads 2和总reads的覆盖情况。
  - 直方图显示了正向链基因S100A9的reads 1或reads 2与注释PAS之间的距离。
  - IGV的截图显示了反向链基因DUSP1的reads 1、reads 2和总reads的覆盖情况。
  -  IGV的截图显示了反向链基因DUSP1的reads 1、reads 2和总reads的覆盖情况。

![](https://pic.imgdb.cn/item/66e242bed9c307b7e91f8df4.png)

在单细胞3' RNA测序中，大多数方法和平台主要关注reads 2，而忽视了reads 1中的数据。reads 1中的cDNA能够捕获接近poly(dT)序列的区域，并可用于精确地检测PAS。