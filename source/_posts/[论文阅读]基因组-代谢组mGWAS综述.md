
---
title: 基因组-代谢组mGWAS联合分析综述
date: 2024-12-16 19:55:32
categories: 论文阅读
cover: /img/cover6.jpg
tags: 多组学
description: "基因组-代谢组mGWAS联合分析综述"
---



# 代谢组学综述

[Metabolic GWAS-based dissection of genetic bases underlying the diversity of plant metabolism](https://onlinelibrary.wiley.com/doi/10.1111/tpj.14097)

[Metabolite-based genome-wide association studies in plants]()

focus水果：[Limitations and advantages of using metabolite-based genome-wide association studies: Focus on fruit quality traits](https://www.sciencedirect.com/science/article/pii/S0168945223001656?via%3Dihub)

focus植物育种：[Recent applications of metabolomics in plant breeding]()

focus果树:[Research Progress and Trends in Metabolomics of Fruit Trees](https://webofscience.clarivate.cn/wos/alldb/full-record/WOS:000796372500001)

[Exploring the Diversity of Plant Metabolism](https://webofscience.clarivate.cn/wos/alldb/full-record/WOS:000454428700012)

[Metabolomics: a systems biology approach for enhancing heat stress tolerance in plants](https://webofscience.clarivate.cn/wos/alldb/full-record/WOS:000595005100001)

Metabolic GWAS-based dissection of genetic bases underlying the diversity of plant metabolism

NC:[GWAS, MWAS and mGWAS provide insights into precision agriculture based on genotype-dependent microbial effects in foxtail millet](https://www.nature.com/articles/s41467-022-33238-4)



# Metabolic GWAS-based dissection of genetic bases underlying the diversity of plant metabolism



2018年 《基于代谢 GWAS 的植物代谢多样性遗传基础剖析》

基于**质谱**的分析系统和**基因组测序技术**的发展。GWAS的概念扩展到了代谢组的研究，产生了**mGWAS**，是全球识别植物代谢多样性遗传决定因素的最强大工具之一。

最近，mGWAS已经在**各种物种**中进行了持续改进，提供了对代谢多样性遗传基础的更深刻见解。

- 我们首先总结了GWAS及其基于统计方法和群体的发展。
- 由于靶向性状的变异对GWAS至关重要，我们回顾了代谢多样性及其在群体和个体层面的兴起。
- 随后，讨论了mGWAS在植物中的应用及其相应的成就。
- 我们还讨论了基于mGWAS的多维分析的当前知识以及对代谢多样性的新见解。

## Introduction



每个植物个体的代谢组受到其发育阶段、组织和环境刺激的显著影响

> 植物由于其定居性，能够产生**数量庞大的代谢物**，估计有10万到100万种，但**每个物种仅生产其中的一部分**。大多数代谢物在不同物种中表现出特异性的积累。此外，研究发现，即使**在同一物种内**，**代谢物的种类和数量的变异**也比之前预期的要大得多。这些代谢物的生成受到植物的发育阶段、不同组织以及环境条件的显著影响。



- 要点

  - 植物代谢组的多样性源于基因组进化、遗传多样性、发育阶段和环境刺激。

  - mGWAS是识别影响代谢多样性的常见遗传变异的强大工具。

  - 通过精心设计的方法和/或群体来发展GWAS，将为解码代谢多样性的遗传基础（包括罕见变异）提供新的机会。

  - 基于mGWAS的多维数据分析对于增强我们对代谢多样性及其相应遗传基础的理解至关重要。

- **未解问题**
  - 我们如何高效地识别结构相似但功能不同的代谢物的生物功能多样性？
  - 不同修饰对代谢物的生化和生物功能有何影响，是否存在普遍规律？
  - 我们如何全面解析代谢途径并以转录后、翻译后和/或表观遗传的方式表征基因功能？
  - 基于不同条件下各个个体代谢物比例的mGWAS对于解析代谢响应环境刺激的机制是否具有强大效力？

## The Development of GWAS

 2005 年首次成功应用 GWAS，然后被广泛应用于解析复杂表型的遗传基础，涵盖了人类和动物的疾病，以及植物的生理和农业性状。

- 刚开始存在的挑战
  - 群体结构和亲缘关系导致的虚假关联问题。
  - 混合线性模型（MLM）作为主要方法，有效纠正偏差。
  - 开发多位点混合模型以应对复杂性状。
- 局限性和创新
  - SNP 基于的 GWAS 面临多重测试惩罚和忽视 SNP 互作的问题
  - 开发了单倍型基于 GWAS、基因基于 GWAS 和基于 A−D 检验的 GWAS，以提高识别能力和统计功效。

## The Rise of Metabolic Diversity

 展示了不同物种的GWAS研究数量

![](https://pic.imgdb.cn/item/676a5d53d0e0a243d4e92662.png)



随着next-generation sequencing和high-throughput phenotype screening筛选 technologies的进步，GWAS全面研究了各种性状，从individual morphological形态scale尺度  (plant height, yield, heading date, etc.)到interaction with various environmental stimuli(abiotic or biotic stresses)

但是呢，GWAS研究出来的QTLs有限，因为相比于代谢物之间的variations来说，不同品种间性状的variation非常的狭隘，代谢物的就非常丰富、而且大部分都有定量

- 植物的代谢多样性是基因组进化和遗传多样性以及环境刺激的结果。
  - Development- and environment-dependent diversity of metabolites may be associated with their biochemical and biological functions resulting from spatial−temporal and/or environment-effected expression of corresponding genetic determinants. 
  - **植物中各种化学物质的多样性会随着植物的生长阶段和所处环境的变化而变化。这些变化影响了这些化学物质在植物中的具体作用，因为不同的基因会在不同的时间、地点或环境条件下被激活或关闭。**

| **类别**                                         | **内容**                                                     | **例子/研究引用**                                            |
| ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **代谢多样性的来源**                             | 植物代谢多样性源于基因组进化、遗传多样性以及环境刺激。       | -                                                            |
| **特定代谢物类：Cucurbitacins**葫芦素            | - 结构特征：四环cucurbitane核骨架的高度多样化三萜类化合物。 - 分类：已发现12类，包括Cucurbitacins A–T。 - 积累特性：各物种主要苦味化合物不同，如Cucurbitacin C仅在黄瓜中发现。 - 遗传基础：CYP基因的保守合成位点及物种特异性CYP缺失。 | Chen et al., 2005; Panosyan et al., 1985; Da Costa and Jones, 1971; Shang et al., 2014; Zhou et al., 2016 |
| **特定代谢物类：Strigolactones (SLs)**独脚金内酯 | - 功能：调控植物整体架构的植物激素。 - 合成途径：all-trans-β-carotene异构化为9-cis-β-carotene，进一步转化为carlactone (CL)。 - 关键酶：细胞色素P450 AtMAX1对活性SL的合成至关重要。 - 遗传变异：两个AtMAX1同源基因的重排导致SL含量变异。 | Gomez-Roldan et al., 2008; Umehara et al., 2008; Alder et al., 2012; Waters et al., 2012; Booker et al., 2005; Cardoso et al., 2014 |
| **基因组进化机制**                               | - 机制：转座子插入、基因重复与发散、基因丧失等。 - 影响：促进代谢路径的分歧进化，导致代谢物多样性。 | Kobayashi et al., 2004; Xu et al., 2017; Zhang, 2003; Palmieri et al., 2011 |
| **作物改良的影响**                               | - 人类选择压力影响代谢进化。 - 例子：番茄育种中选择低苦味水果，减少苦味化合物含量。 | Zhou et al., 2016; Zhu et al., 2018                          |
| **个体代谢多样性的决定因素**                     | - 决定方式：发育依赖和环境刺激依赖。 - 代谢物多样性通过糖基化和酰基化等修饰反应产生定性多样性。 - 例子：Luteolin 6-C-glucoside在水稻叶片中呈发育梯度累积。 | Koes et al., 1994; Stobiecki, 2000; Lepiniec et al., 2006; Dong et al., 2015 |
| **环境刺激对代谢的影响**                         | - 影响因素：干旱、营养缺乏、光照、温度等。 - 代谢反应：不同环境刺激诱导特定代谢物的积累。 - 例子：冷适应下20种类黄酮flavonoids的累积增加；病原体感染诱导epigallocatechin等flavonoids的积累。 | Sperdouli and Moustakas, 2012; Jiang and Fu, 2007; Zoratti et al., 2014; Jaakola and Hohtola, 2010; Schulz et al., 2015; Koskimäki et al., 2009 |

- Cucurbitacins

![](https://pic.imgdb.cn/item/676a63c7d0e0a243d4e9342b.png)



## Deciphering the Genetic Bases of Metabolic Diversity with mGWAS

- 过去，有大量的反向遗传学的研究来剖析代谢途径。 
  - **从基因功能入手，解析代谢途径**
  - 比如使用RNA-seq来发现某个基因表达差异，与某个代谢物相关。**更加精确**
  - 通过这种比较基因组分析和代谢数据相结合，来重新构建物种的相关代谢通路。

最近，物种内自然发生的代谢多样性和潜在的遗传决定因素吸引了越来越多的研究兴趣。某些代谢性状是由多个基因一起控制的，多基因遗传。特别是在植物中。

> 比如：mQTL（metabolic Quantitative Trait Loci）映射，研究者们发现了VTE3基因的表观等位基因自然变异，这决定了番茄果实中维生素E的积累。

- **mGWAS的应用扩展**：

  - 为了识别**自然群体中更广泛遗传变异对代谢多样性的影响**，mGWAS最初在模式物种拟南芥Arabidopsis thaliana中应用，随后成功扩展到多个其他物种

  - 这些研究涵盖了**初级代谢物**（如糖类、氨基酸等）和**次级代谢物**（如flavonoids等），涉及植物的营养组织（如叶片）和生殖组织（如花朵）。

- **农业性能与代谢物变异的不同遗传控制**：
  - 以前的研究都表明，农业性状（如产量、抗病性等）由**众多小效应位点**控制，每个位点对性状的影响较小。
    - 比如水稻的产量取决于几千个基因
  - 初级代谢物的含量通常由许多具有较小效应的位点决定。
  - 但是，**次级代谢物**的**自然变异**通常由**少数大效应位点**控制，即每个位点对代谢物含量的影响较大。
    - 比如某个植物的某个抗生素含量就跟少数几个基因有关，这个从传统的GWAS中就分析不出来
  - 此外，代谢遗传架构中存在决定大量代谢物变异的**“热点**”基因区域，这些区域受到自然选择的影响。
    - 某些基因区域控制多个代谢物的生产，这些区域因为在抗病过程中起关键作用而在进化中被强化和保留。

- **衍生性状**
  - 代谢物之间有相关性
    - 在植物中，许多代谢物在相同或相关的代谢途径中被共同调控。它们可能经历相似的化学反应或修饰过程，甚至在不同的修饰方式之间竞争相同的底物。
  - 使用一些衍生性状
    - 基于代谢物的绝对含量计算得出的，例如相关代谢物的总和或两个代谢物之间的比例。
  - 衍生性状和mGWAS
    - Angelovici等人通过检测氨基酸的绝对含量，识别出一个由多个相互连接的氨基酸组成的网络，并利用衍生性状（如氨基酸比例）进行GWAS，从而更有效地识别出影响这些氨基酸含量的基因。
- 此外还有 comparative GWAS，植物物种之间共享的“共同”基因座使用mGWAS，根据物种间代谢性状的共调控来识别候选基因。

# Limitations and advantages of using metabolite-based genome-wide association studies: Focus on fruit quality traits

2023年 《使用基于代谢物的全基因组关联研究的局限性和优势：关注水果品质性状》

 过去通过**Linkage**分析了大量的物种中代谢物数量性状位点QTL。

现在下一代测序和高通量基因分型技术，mGWAS成为识别多基因农作物性状中遗传变异的有力工具。

在水果中，水果风味是香气挥发物和味道的复杂相互作用，是糖和酸比是风味接受度的关键参数。

这篇文章回顾了mGWAS技术在水果中与风味代谢物相关的精确基因多态性的研究进展。

- 这篇文章自己的工作：
  - **柚子品种的mGWAS**：在对194个柚子品种进行的mGWAS研究中，研究者们调查了成熟果实中单个初级代谢物和脂质代谢物的遗传控制。
  - **发现的关联**：共识别出了14种初级代谢物（包括氨基酸、糖类和有机酸）的667个关联，以及47种脂质对应的768个关联。
  - **候选基因**：通过这些关联，研究者们发现了与果实质量相关的重要代谢物（如糖类、有机酸和脂质）相关的候选基因，为进一步的功能验证和作物改良提供了依据。



## Introduction

遗传学的主要目标是研究基因型和表型之间的关系。尽管复杂性状的很大一部分变异是由于遗传变异造成的，但遗传变异和性状之间的机制通常知之甚少。

代谢物在植物的基因型和表型之间的关系中起着至关重要的作用。

培育精英品种的有效操作需要了解途径的遗传和生化基础以及控制这些性状的调节系统。

- 代谢组学分析结合下一代测序技术
  - mQTL 方法一直是剖析农艺性状遗传基础的非常成功的工具，特别是研究营养品质的遗传决定因素
  - mGWAS





## 2 限制mGWAS的分析因素

### 2.5 GWAS analysis to identify metabolic candidate genes underlying fruit quality traits

对于水果的性状来说，过育种者在过去几十年中主要通过选择颜色、硬度、外观和保鲜期等特性来改良水果的质量。这些选择标准虽然提升了水果的市场吸引力，但在这个过程中，水果的风味和香气性状却被忽视或减少了。

通过GWAS和代谢组的结合，就可以通过找到风味/香气相关的基因，然后从野生种中找到这些控制化合物合成的候选基因，引入到现代栽培品种中。



### 2.6 Metabolomics-based GWAS in citrus fruits

对于194种不同品种的柑橘品种，分析了150种化合物（55种初级代谢物和95种脂质）

![](https://pic.imgdb.cn/item/676a81ebd0e0a243d4e94265.png)

