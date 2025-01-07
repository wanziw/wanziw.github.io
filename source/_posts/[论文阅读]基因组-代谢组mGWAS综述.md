
---
title: 基因组-代谢组mGWAS联合分析综述
date: 2024-12-24 19:55:32
categories: 论文阅读
cover: /img/cover6.jpg
tags: 多组学
description: "基因组-代谢组mGWAS联合分析综述"
---

[toc]



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

# 综述内容

## 框架

- 第一篇Metabolic GWAS-based dissection of genetic bases underlying the diversity of plant metabolism

- ```
  The Development of GWAS
  The Rise of Metabolic Diversity
  Deciphering the Genetic Bases of Metabolic Diversity with mGWAS
  mGWAS-Based Multi-dimensional Analysis
  ```

- 第二篇Limitations and advantages of using metabolite-based genome-wide association studies: Focus on fruit quality traits

```
Critical factors to consider in mGWAS analysis. General limitations
Confounding factors in GWAS
Allelic heterogeneity
 Low GWAS statistical power
 Rare causal variants
 GWAS analysis to identify metabolic candidate genes underlying fruit quality traits
 Metabolomics-based GWAS in citrus fruits
```







- 第三篇Research Progress and Trends in Metabolomics of Fruit Trees

   

```
Metabolomics Strategies and Key Techniques
Metabolomics Strategies  代谢组学策略
Key Techniques in Metabolomics
Data Processing  数据处理
Application of Metabolomics in Fruit Trees

```

- 第四篇 pdf

```
Plant metabolomics: an overview
Current analytical techniques for plant 
metabolomics research
Key steps and workfow for plant 
metabolome analysis
Metabolomic studies in plant stress 
response
```





**1. 基因组学与GWAS：代谢性状遗传基础的探索**

参考内容：第一篇的 “The Development of GWAS” 和 “Deciphering the Genetic Bases of Metabolic Diversity with mGWAS”，第二篇的 “GWAS analysis to identify metabolic candidate genes underlying fruit quality traits”

- 主要是第一篇

```
GWAS is an observational study of a genome-wide set of common genetic variants in experimental populations, to identify variants associated with a trait. Klein et al. successfully performed the first GWAS and identified a variant in the Complement Factor H gene strongly associated with age-related macular degeneration (Klein et al., 2005). In the last decade, GWAS has been proven to be powerful in dissecting the genetic basis for variation in complex phenotypes, including disease in humans and animals (Pickrell et al., 2016; Soldner et al., 2016; Duncan et al., 2017; Jin et al., 2017; Pasaniuc and Price, 2017; Visscher et al., 2017), and physiological and agricultural traits of plants (Huang et al., 2010; Tian et al., 2011; Horton et al., 2012; Chen et al., 2016; Yano et al., 2016; Xiao et al., 2017). However, population structure and unequal relatedness among individuals result in spurious associations and false discoveries in GWAS. Methodologically, much effort has been made to address population stratification (Devlin and Roeder, 1999; Abecasis et al., 2000; Liu et al., 2016). In mixed linear models (MLM), population structure is fitted as a fixed effect, whereas kinship among individuals is incorporated as the variance−covariance structure of the random effect for the individuals (Yu et al., 2006; Zhao et al., 2007). The MLM method has become the most popular method for GWAS because of its demonstrated effectiveness in correcting the inflation from many small genetic effects and controlling the bias of population stratification. Subsequently, a series of models based on MLM has been developed to more efficiently and accurately identify associations between variants and traits (Korte et al., 2012; Segura et al., 2012; Loh et al., 2015). Generally, MLM-based models are carried out with single-locus tests to identify associations between polymorphisms and traits. However, for complex traits determined by several large-effect loci, this approach may not be appropriate, especially in the presence of population structure. The application of multi-locus mixed models could lead to the identification of new causative loci with promising performance (Segura et al., 2012; Wen et al., 2017). Despite the contribution of single nucleotide polymorphism (SNP)-based GWAS to the dissection of genetic bases underlying complex traits in various species, SNP-based GWAS incurs a severe penalty for multi-testing due to the overlooked interactions between SNPs within a gene and weak signals aggregating within related SNP sets. To limit the false discovery rate associated with GWAS analyses, haplotype-based GWAS with high statistical power has been developed to identify causal haplotypes with specific combinations. Haplotype-based GWAS was able to identify new candidates for complex traits, although its power for detecting quantitative trait loci (QTLs) is much lower than that of SNP-based GWAS, especially for QTLs with low minor allele frequencies (Sato et al., 2016). Moreover, gene-based GWAS has also been developed, involving all variants within a gene (Yano et al., 2016; Zhang et al., 2016). The above-mentioned methods are based on the assumption that the phenotype or marker effect will follow a typically normal distribution. GWAS based on the Anderson−Darling (A−D) test is a complement to MLM-based GWAS methods, especially for complex quantitative traits determined by moderate effect loci or rare variants, and with abnormal phenotype distribution (Yang et al., 2014a). To refine the genomic localization of causal variants identified in GWAS, fine-mapping strategies have been developed by using statistical methods (Schaid et al., 2018).
The essence of GWAS is to identify naturally occurring genetic variance associated with targeted traits. Although the method of GWAS is a means to discover candidate QTLs, the population used for GWAS essentially determines whether there are causative genes and variants underlying diversity in traits. For example, distinct genes have been identified to be responsible for natural variation in rice heading date in GWAS with different populations (Huang et al., 2010; Yang et al., 2014b; Huang et al., 2015; Yano et al., 2016). Recently, kinds of genetic populations have been used in GWAS to efficiently identify causative genes for agricultural traits. For instance, approximately 1500 diverse varieties of hybrid rice were used to elucidate the genetic basis of rice heterosis (Huang et al., 2015). In addition to the natural populations used in GWAS, well designed artificial populations have been developed to efficiently identify genetic variants determining complex traits. For example, a nested association mapping populations (NAM) of maize, derived from crosses between a reference line and other founder inbreds, have been used in GWAS of developmental traits and resistance to pathogens with improved mapping resolution (Kump et al., 2011; Poland et al., 2011; Tian et al., 2011; Li et al., 2016; Wu et al., 2016). However, the extremely unbalanced parental compositions might dilute the GWAS efficiency (Xiao et al., 2017). To thoroughly intercross and effectively balance the contributions of all founder lines, the advanced generation intercross (MAGIC) populations of rice were established in various species (Kover et al., 2009; Huang et al., 2012; Bandillo et al., 2013; Dell'Acqua et al., 2015; Islam et al., 2016). The application of NAM or MAGIC populations is largely limited, due to the requirement for extensive field and laboratory effort. The random-open-parent association mapping (ROAM) population, consisting of different existing RIL populations, improves genetic resolution and statistical power to identify variants with minor effect and low frequency (Giraud et al., 2014; Xiao et al., 2016).
Over the last decades, numerous reverse genetic studies have been carried out to dissect metabolic pathways (Zhao et al., 2016; Perchat et al., 2018; Tian et al., 2018). Meanwhile, genes determining the accumulation of compounds with vital biological functions have also been characterized in studies of phenotypic traits (Cardoso et al., 2014; Yang et al., 2017; Arisz et al., 2018; Song et al., 2018). Recently, improved sequencing technologies have provided new chances to dissect metabolic pathways. For instance, Capuri et al. identified two missing enzymes in the biosynthesis of vinblastine, using RNA-seq data (Caputi et al., 2018). Furthermore, with the increasing number of genome sequences available from closely or more distantly related species, it is becoming possible to combine comparative genomic analysis with metabolic data in gene identification and pathway elucidation (Denoeud et al., 2014; Huang et al., 2017). To dissect the mechanism of rubber production and species adaptation, Tang et al. performed a comparative genomic analysis, using genome and transcriptome sequencing with six cultivars of rubber trees. They characterized the crucial role of a striking expansion of the REF/SRPP (rubber elongation factor/small rubber particle protein) gene family and its divergence into several laticifer-specific isoforms in rubber biosynthesis. Moreover, the stringent control of ethylene synthesis under active ethylene signalling and response in laticifers resolved a longstanding mystery of ethylene stimulation in rubber production (Tang et al., 2016). Recently, the naturally occurring metabolic diversity within species and the underlying genetic determinants have attracted increasing research interests (Luo, 2015). Studies with natural or artificial populations in several species discovered that plant metabolism is moderately inheritable and shows polygenic inheritance (Chen et al., 2014; Alseekh et al., 2015; Soltis and Kliebenstein, 2015). Metabolites displayed high heritability and constant diversity within experimental populations, making the metabolome of plants an ideal target trait for population genetics studies. There are legions of examples of population genetic studies on the plant metabolome, for example, mQTL mapping with molecular markers identified natural variation in epialleles of VTE3, determining vitamin E accumulation in tomato fruits (Quadrana et al., 2014). Ultra high-density genetic maps have provided fresh impetus toward the identification of tremendous numbers of genes underlying metabolic diversity between parents (Gong et al., 2013; Wen et al., 2015).
To identify effects of more widespread genetic variants on metabolic diversity across natural populations, mGWAS was initially applied in the model species Arabidopsis thaliana and then successfully performed in and extended to a number of other species, especially important crops. These studies covered primary metabolites (Strauch et al., 2015; Angelovici et al., 2016; Du et al., 2018) and secondary metabolites (Dong et al., 2015; Peng et al., 2016, 2017), ranging from vegetative tissue (Chen et al., 2014; Matsuda et al., 2015; Fang et al., 2016) to reproductive tissue (Wen et al., 2014; Zhou et al., 2016; Zhu et al., 2018). Generally, agricultural performance is under the control of numerous loci of small effects (Huang et al., 2010). However, natural variation in secondary metabolites tends to be controlled by a small number of loci with large effects (Chen et al., 2014), while the contents of primary metabolites are generally determined by many loci of smaller effects (Rowe et al., 2008; Chan et al., 2010; Wen et al., 2015). In addition, a common feature in the genetic architecture of metabolism is the presence of ‘hotspots' of major genes/genome regions determining the natural variation in large sets of metabolites (Chan et al., 2010; Knoch et al., 2017). More detailed evaluation revealed that some of the hotspots in Arabidopsis are within the regions of the genome previously identified as being subject to recent strong positive selection (selective sweeps) and regions showing trans-linkage to these putative sweeps, suggesting that selective forces have impacted genome-wide control of Arabidopsis metabolism (Chan et al., 2010). Causative genes identified in GWAS of complex traits tend to be regulatory genes, such as transcriptional factors (Huang et al., 2010; Yano et al., 2016). However, most of the causative genes for metabolic diversity encode enzymes involved in the production of targeted compounds (Chen et al., 2014; Wen et al., 2014; Matsuda et al., 2015; Wen et al., 2015; Chen et al., 2016). Hence, it is much easier for researchers to predict gene candidates in mGWAS. Although crucial roles of several transcriptional factors have been revealed in mGWASs (Okada et al., 2009; Yamamura et al., 2015; Zhu et al., 2018), the genetic bases for the diversity in regulation of metabolite accumulation remain to be unveiled. In addition, to date, mGWAS strategy is applied in limited species, with well sequenced populations available (Chen et al., 2014; Wen et al., 2014; Angelovici et al., 2016). Recently, a cost-effective approach for low-coverage sequencing-based GWAS has been developed (Wang et al., 2016). In such a strategy, low-coverage sequence data combined with imputation-based methods were used for genotype calling, which provides easy resolution of haplotypes and higher genotype calling accuracy (Wang et al., 2016). This strategy will be helpful for further GWAS on both metabolic and phenotypic traits in special species, such as medicinal plants.
In contrast with the weak linkage among agricultural traits, tremendous numbers of metabolites are tightly correlated due to the co-regulation of natural products in the same pathway, the related reactions in metabolic pathways, the same modification of structurally similar compounds, and the competition for substrates of different modifications. Aschard et al. found that principal-component analysis (PCA)-based approaches could maximize the power of GWAS on correlated phenotypes (Aschard et al., 2014). Similar strategies may also be helpful for dissection of genetic bases for diversity in correlated compounds. In addition, derived traits generated from absolute levels of metabolites provided new insights into a metabolic network, including the sum of related metabolites or the ratio of two related compounds (Sauer et al., 1999; Weckwerth et al., 2004; Wentzell et al., 2007). Exploring the association of metabolites could also contribute to the dissection of metabolic pathways with mGWAS. For instance, Angelovici et al. detected the absolute content of 18 free amino acids and identified a network of 12 connected amino acids. Derived traits were calculated as a ratio of connected metabolic pairs or as a ratio of a single amino acid, to its fully or partially connected metabolic group (Angelovici et al., 2016). Network-guided GWAS based on the derived traits improved identification of causative genetic determinants affecting free amino acids. The requirement of the absolute content of metabolites may limit the application of network-guided GWAS, especially for GWAS based on metabolomic data.
Over the last decades, fruit quality traits defined as flavor, aroma, mount-feeling, and postharvest properties have been selected for breeders by considering a diverse of properties such as color, firmness, appearance or shelf life. This historical selection has result in a genetic erosion of flavor/aroma traits in modern cultivars, therefore a loss of variants controlling fruit quality directly associated to metabolite level (Giovannoni, 2018). Thus, in general, the current modern cultivars lack in compounds that impact on those fruit quality traits. This dilution of flavor/aroma compounds should be correctable by restoring or introducing specific metabolites (desirable trait) from old cultivars or wild species to modern commercial cultivars. As described above, the combination of GWAS analysis with metabolomics have been successfully used to discover genes underlying fruit metabolite content of flavor/aroma impact compounds. Once the candidate genes controlling the synthesis of these compounds, their superior alleles can be re-introduced in modern cultivars.
```



**2. 代谢组学：技术、策略与应用**

参考内容：第三篇的 “Metabolomics Strategies and Key Techniques”，第四篇的 “Current analytical techniques for plant metabolomics research”

主要是第三篇

```
Metabolomics Strategies
Metabolites in plants can generally be divided into primary and secondary metabolites. Primary metabolites are the basic material conditions necessary for the growth and development of organisms, while secondary metabolites are metabolites produced only at a certain stage or period of growth of an organism (Koch, 2004; Carreno-Quintero et al., 2013). Depending on the purpose of the experiment, researchers can choose individual metabolomics strategies, including targeted metabolomics, non-targeted metabolomics, pseudo-targeted metabolomics, and widely targeted metabolomics.

Targeted metabolomics assays are performed on known compounds with targeted extraction methods and high-purity standards to quantify the target metabolism. Generally, targeted metabolomics focuses on fewer compounds and can be searched directly in classified databases, for example, databases for glycans and lipids such as LipidMaps and LipidBank (Cajka and Fiehn, 2016). Non-targeted metabolomics assays are performed on unknown compounds. It covers as many compounds of different properties and classes as possible in the extraction and detection, with a relatively broad coverage of substances. However, both the qualitative and quantitative properties of compounds are compromised by the lack of standards. Generally, non-targeted metabolomics studies are used to screen for differential metabolites in different treatments, and targeted metabolomics studies are used for the next more precise study.

To overcome the disadvantages of non-targeted metabolomics, widely targeted metabolomics, also known as second-generation targeted metabolomics, allows for the simultaneous detection of thousands of substances by the establishment of a database of thousands of metabolite specimens (Wei et al., 2013). Pseudo-targeted metabolomics is a quantitative ion selection algorithm based on untargeted metabolomics. It is used to perform quantitative ion selection for all detected metabolites. The ion-pair information of metabolites is obtained by high-resolution mass spectrometry (HR-MS), and the abundance of metabolites is measured by targeted multiple reaction monitoring (MRM). The method has high coverage, good linearity, and reproducibility and does not require standards to limit the metabolites’ detection. Both known and unknown metabolites in the sample can be measured (Zheng et al., 2020).

Spatial metabolomics integrates traditional metabolomics technology and MS imaging technology, which can not only identify what substances are contained in a sample and their contents as traditional metabolomics but also detect the spatial distribution information of compounds in a single experiment to achieve qualitative and quantitative positioning at the same time (Li et al., 2018).
a
Key Techniques in Metabolomics
The exploration of the diversity of fruit tree metabolism and potential molecular mechanisms by which fruit tree cells control their own chemical composition depends on the advances of analytical methods.

Sample Processing
Samples should be collected representatively, with priority given to normally developing plants. Furthermore, 3–6 individuals should be selected as a source of biological replicates to avoid differences due to excessive individual differences. Ice boxes or ice packs should be used to collect samples in the field to reduce the degradation of metabolites by enzymes that are still active after sample collection. At the same time, samples should be collected with certain accuracy, and the samples of the experimental and control groups should be consistent in terms of time (Urbanczyk-Wochniak et al., 2005), site, and processing conditions, as far as the experiment allows. If the kernels are not studied, it should be removed with a scalpel in a low-temperature metal bath on an RNAase reagent-treated bench. For the study of the peel, the pulp should be taken as less as possible (Montefiori et al., 2009; de Godoy et al., 2013; Rudell et al., 2017). Freezing of the whole fruit should be avoided if possible during the sampling process, which will make the subsequent freeze-drying and grinding work difficult, and once the whole fruit is freeze-thawed, the whole experimental results will be affected. Then, the sample will be stored in a suitable volume of a centrifuge tube, marked and quickly put into liquid nitrogen for precooling, and then put into −80°C refrigerator for storage. Note that the samples should not be stored in tin foil, self-sealing bags, Ziploc bags, plastic bags, etc.; such packaging is easy to break under low temperature or in the process of transportation and easy to make the markings blurred, resulting in sample confusion.

The metabolites are usually extracted separately with water or organic solvents (e.g., methanol, chloroform, etc.) to obtain aqueous and organic solvent extracts, thus separating the non-polar lipophilic phase from the polar phase. To enrich the concentration of metabolites during the study, the process of vacuum concentration and spin-drying of the extracts before redissolution is often added. In the process of sample analysis method establishment, the optimal method can be figured out by trying different combination of extraction solvents, extraction temperatures, ratios of sample and solvent, redissolved solvent, mobile phase gradients, and mobile phases and by the controlled variable method (Kim and Verpoorte, 2010). The detection of non-targeted metabolites should include as many compound peaks as possible, and the detection of targeted metabolites should ensure that all concerned metabolites can be detected. The sample sequence requires the insertion of quality control samples at intervals of 10 or 20 during the detection by liquid chromatography-MS (LC-MS), which generally includes all compounds of the sample being tested or a mixture of a representative batch of samples. In addition, compounds not contained in the fruit trees are added as internal standards during the extraction of the samples to calibrate the loss of sample compounds during the extraction and detection process and thus to correct the peak areas of other compounds. In vivo direct-immersion solid-phase microextraction followed by gas chromatography-time-of-flight mass spectrometry method (SPME GC × GC-TOF-MS) can detect volatile compounds directly without extracting the compounds (Risticevic et al., 2016, 2020).
Analysis
Chromatography is used for the purpose of separating metabolites according to the different affinities of compounds and columns and is generally divided into LC and gas chromatography (GC). LC is used to detect non-volatile compounds, polar compounds, thermally unstable compounds, and high-molecular-weight compounds (including proteins, peptides, and polymers). The mobile phase generally uses methanol, acetonitrile, water, or isopropanol; the added acid is generally acetic acid or formic acid, inorganic acid cannot be used (inorganic acid may corrode the pipeline); the added base is generally ammonium hydroxide or ammonia, generally does not use metal bases (will corrode the pipeline). Trifluoroacetic acid (TFA) helps to improve the separation of the liquid phase but will produce ion suppression in the positive and negative ion modes of MS. Triethylamine/trimethylamine (TEA/TMA) contributes to the formation of negative ions. GC can be used for the detection of volatile compounds, the mobile phase is an inert gas, and samples with a certain vapor pressure and good stability at column temperature can be detected. Substances with low volatility and easily decomposed by heat can be transformed by derivatization into derivatives with high volatility and good thermal stability for detection. N-methyl-N-trimethylsilyl trifluoroacetamide (MSTFA) and methoxamine hydrochloride are often used as derivatization reagents, as preliminary studies have shown that these compounds are the most suitable for the derivatization of plant metabolites (Fiehn et al., 2000).

Mass spectrometry separates some of the ions based on the mass to charge ratio. The ions pass through the analyzer and are separated according to different mass to charge ratios. Ions with the same mass to charge ratio are clustered together to form a mass spectrogram. Commonly used mass spectrometers are triple quadrupole mass analyzer (Yost and Enke, 1978), time-of-flight mass analyzer, ion trap mass analyzer, and electrostatic field orbital trap. The triple quadrupole mass analyzer consists of four straight rod electrodes suspended equidistantly parallel to the axis. Under the action of a certain DC/VC, ions with m/z meeting certain requirements can pass through the quadrupole to the detector, while other ions are filtered out. The advantages of the triple quadrupole are light weight, small size, and low cost. The time-of-flight mass analyzer uses pulses to extract ions from an ion source. The ions are accelerated by an accelerating voltage, have the same kinetic energy, and enter the drift tube. Ions with a small mass to charge ratio are the fastest and reach the detector first. Larger ions reach the detector last. The advantages of TOF MS are a wide range of mass to charge ratio of the detected ions, high sensitivity, and suitability for secondary tandem MS. A fast scanning speed is suitable for studying very fast processes. The principle of an ion trap mass analyzer is similar to that of quadrupole mass analyzer. When the HF voltage amplitude and HF voltage frequency are fixed to a certain value, only ions with a certain mass to charge ratio can be stabilized on a certain track in the trap. By rotating and changing the electrode voltage, different m/z ions fly out of the trap and reach the detector. The advantage of ion trap mass spectrometer is that a single ion trap can realize multistage “time” tandem MS, simple structure, low price, high cost performance, high sensitivity, and large mass range. The electrostatic field ion orbitrap is where analytes are ionized in an ion source and then sequentially enter a quadrupole, a C-trap, and an Orbitrap. The electrostatic field ion orbitrap mass spectrometer can perform high precision mass scans, and it is more stable than other mass analyzers.

Mass spectrometry characterizes compounds by different characteristic ions of different compounds. Chromatographic methods enhance the coverage of metabolites and improve the quantitative accuracy of MS. The most commonly used separation and analysis methods are LC-MS (Vos et al., 2007), GC-MS (Lisec et al., 2015). For LC-MS and GC-MS methods, internal standards are added before sample processing to correct errors caused by sample pretreatment and instrument response.

Data Processing
Data processing in metabolomics generally consists of two major steps, namely, data preprocessing and statistical analysis (Ma and Qi, 2021). Data preprocessing includes steps such as removing system noise signals, removing disturbing signals caused by system instability, and removing operational errors to provide a more reliable dataset for the next statistical analysis. Prior to formal data processing, tools such as XCMS, MZmine, and MarkerView are used to process the original peak area and other data for non-targeted metabolomics data analysis. The first step of the statistical analysis is unsupervised multivariate statistical analysis, usually using the principal component analysis (PCA). The second step may be the univariate statistical analysis to screen for variables with statistically significant differences in different groups. The third step is a supervised multivariate statistical analysis such as partial least squares discriminant analysis (PLS-DA) to select the variables that contribute more to the classification of the sample, i.e., screen for markers.

The purpose of the PCA analysis (Shaffer, 2002) is to find specific values that produce differences in a large amount of sample data. PLS-DA analysis will classify samples into groups, which is good for finding the similarities and differences between sample groups; orthogonal partial least squares discriminant analysis (OPLS-DA) can also distinguish the group differences between samples, but this analysis can better focus on some positive correlation data. The results of data analysis are also subject to the t-test and variable importance in projection (VIP) ranking values to screen for differential metabolites. It is generally accepted that variables meeting both P < 0.05 and VIP > 1.0 are differential metabolites. Metabolic pathways can be resolved using databases such as HMDB, KEGG, Reactome, BioCyc, and MetaCyc.

Application of Metabolomics in Fruit Trees
Fruit tree metabolomics has developed rapidly in recent years, and many important research results have been achieved in combination with transcriptomics, genomics, proteomics, quantitative trait locus (QTL), and genome-wide association study (GWAS) (Tables 2, 3). These research results mainly focus on the mechanism of fruit quality formation, metabolite markers of special quality or physiological period, key genes and metabolites of fruit tree resistance to biotic/abiotic stress, the influence of environment on the fruit tree, and fruit tree population genetic basis by combining with QTL and GWAS to narrow down QTL regions, predict candidate genes, construct the regulatory network, etc. (Figure 3).
Metabolomics has developed as an outstanding scientifc 
feld; however, a single analytical technique is not adequate 
to detect and quantify the metabolites (Weckwerth, 2003; 
Templer et al. 2017). Presently, various metabolomic techniques are being applied in plant metabolomics research, as 
discussed in the introduction. Out of these, GC, MS, NMR, 
and HPLC dominate the metabolite tools. Two basic techniques, MS and NMR, are used in modern metabolomics, 
including the generation of metabolomics data. Interestingly, 
NMR is preferred to MS because of its high capacity in 
detecting protein binding sites, direct binding of target proteins, physical properties of ligands, and uncovered protein 
structure coupled with ligands. Metabolite exposure reliant on NMR uses magnetic properties of various nuclei of 
atoms. The diferent applications, such as metabolite profling and fngerprinting, metabolic fux, and atomic structural 
details of diferent biological samples, are integrated with 
NMR. Owing to the non-destructive nature of NMR with a 
smaller molecular weight is widely used to detect metabolites (Eisenreich and Bacher 2007; Kim et al. 2010). Hence, 
this technique is so sensitive, and it has a low abundance of 
biomarkers that causes its limited use. Except for NMR, the 
MS technique has the best sensitivity, and researchers can 
get an extensive range of metabolome data. This technique 
would help researchers to detect molecules and metabolic 
biomarkers that can rebuild metabolic networks and pathways. Diferent ionization methods such as matrix-assisted 
laser desorption/ionization (MALDI-TOF), atmospheric 
pressure chemical ionization (APCI), and electrospray ionization (ESI) were accurately detected by MS (Issaq et al. 
2009). To get accurate results, MS is coupled with various 
techniques such as feld asymmetric waveform ion mobility 
spectrometry (FAIMS), CE, GC, FT-ICR, and LC. Figure 2
indicates the comparison of frequently working analytical 
techniques in plant metabolomics research.
Notably, MS has obtained a progressively vital role in 
the feld of metabolomics and proteomics due to the signifcant progress that has been made in instrument technologies. The frequently used technique for untargeted analysis 
is GC–MS (Rohlof 2015). Sample derivatization was done 
by the GC–MS technique, making the compound volatile; 
however, some compounds are left as underivatized during 
analysis. GC–MS has been recognized as a high-throughput analytical technology with a high rate of sensitivity for 
metabolic profling. GCxGC-TOF–MS enhanced the output through the segregation of co-eluting peaks (Hurtado 
et al. 2017). Higher mass primary and specialized metabolites (<1500 Da) are detected by targeted and untargeted 
techniques facilitated by LC–MS that uses ESI and APCI 
(Turner et al. 2016). Identifcation of several metabolites 
increases peak resolution, and mass accuracy was done in 
a short time with the help of UPLC coupled with QTOFMS (Chawla and Ranjan 2016). In targeted and untargeted 
metabolomics analysis, high-resolution separation of metabolites is mainly done by CE-MS (Ramautar et al. 2019). 
FT-ICR-MS is driven by high-resolution mass analysis that 
provides extensive and reliable detection of metabolites. It 
is also coupled with separation techniques to settle complex 
matrices, and ion separation was also done by this technique 
(Ghaste et al. 2016; Nakabayashi et al. 2016; Lopes et al. 
2017).
Data produced from the above-mentioned techniques are 
processed by Met-Align, PlantMAT, MET-XAlign, METCOFEA, XCMS, and ChromaTOF, etc. (Table 1). Statistical 
analysis of identifed metabolites is followed by using a combination of (1) univariate analysis (Student t test; ANOVA; 
Mann–Whitney U test; Benjamini–Hochberg false discovery 
rate correction; Kruskal Wallis 44%), and (2) multivariate 
analysis (principal component analysis (PCA); partial least 
squares discriminant analysis (PLS-DA); orthogonal partial least squares (O-PLS); high-content screening (HCA); 
heatmap, correlation analysis, neural networks, genetic algorithms, and random forest methods. Currently, several diferent software and online tools are available for metabolome 
analysis, like MetaboAnalyst, MetaboliteDetector, MetaMapR, MetExplore, Cytoscape, g:Profler, Gene-set enrichment analysis (GSEA), Metabolite-set enrichment analysis (MSEA), EnrichmentMAP, Workfow4Metabolomics
```



**3. 基因组学、代谢组学与GWAS的结合：多组学分析的前沿探索**

参考内容：第一篇的 “mGWAS-Based Multi-dimensional Analysis”，第二篇的 “Metabolomics-based GWAS in citrus fruits”

- 第一篇

```
Even though numerous key genes with large effects on the accumulation of metabolites have been characterized with mGWAS, single data type analyses may lead to missing or unreliable information. Moreover, the extent of linkage disequilibrium (LD) in plants often ranges over several hundred kilobases, especially in self-pollinating crops such as rice (Mather et al., 2007), resulting in the inclusion of many candidate genes in a single LD block. Hence, multi-dimensional data analysis is essential for enhancing our understanding of metabolic diversity and its corresponding genetic basis. Multi-dimensional data could be collected from different tissues or conditions, various analysis strategies, and/or multi-omics data.

As we have discussed above, the spatial−temporal and environment-dependent expression of key regulators of metabolic pathways lead to the metabolic diversity at the individual level. Some studies based on metabolome data from different tissues (Chen et al., 2014; Matsuda et al., 2015; Chen et al., 2016) or under different conditions (Wu et al., 2018) have also identified diverse genetic determinants for the same or structurally similar compounds. Although combined mGWAS under different conditions enhanced the power to identify causative genes (Wu et al., 2018), knowledge about the variation in the content ratio of each individual metabolite is still lacking, as well as knowledge about deciphering its genetic basis with mGWAS. However, rigorously designed mGWAS based on metabolite content ratios under different conditions will contribute not only to the understanding of metabolic diversity under constantly changing environments, but also lead to the identification of key regulators for stress responses from the lens of the metabolome.

With the development of genome sequencing and bioinformatics technologies, various strategies have been improved to decipher the genetic diversity of targeted traits, such as association and linkage mapping. Association mapping by GWAS for plants has provided new genetic and biochemical insights into metabolomes. While it is true that GWAS benefits from abundant genetic variants allowing the location of QTL to be inferred with a high resolution, the inherent population structure and presence of rare variants in experimental populations reduce the statistical power of GWAS (Huang et al., 2010). Linkage mapping using artificial populations such as RILs and ILs is likely to be more powerful in identifying alleles with low frequency or small effects in the population (Fridman et al., 2004; Schauer et al., 2006). Hence, combined linkage and association mapping are powerful not only in cross-validating results from one another but also in identifying new causative loci (Luo, 2015). Recent work by Peng et al. provides encouraging evidence for the assumption that joint-linkage and association mapping are powerful not only in cross-validating results from one another but also in complementing each other in identifying new causative loci (Peng et al., 2016). However, association mapping and linkage mapping in this work were performed with distinct populations. Newly designed multi-parent mapping populations, such as NAM, MAGIC, and ROAM, are suitable for joint-linkage and association mapping (Xiao et al., 2017).

Multi-dimensional analyses have been increasingly used to provide clues for understanding biological mechanisms, since combining multiple datasets can compensate for missing or unreliable information in any single data type (Ritchie et al., 2015). Combined analyses with metabolic and transcriptomic data have been utilized to dissect various metabolic pathways (Itkin et al., 2013; Cardenas et al., 2016). Taking advantage of available experimental populations, transcriptomic data were collected from 240 lettuce accessions sampled from the major horticultural types and wild relatives. Nine eQTLs were identified in GWAS to regulate genes associated with flavonoid biosynthesis (Zhang et al., 2017). Multi-dimensional analysis of genomes, transcriptomes, and metabolomes could be more powerful to provide new insights into metabolic diversity, using large population collections. For instance, Zhu et al. performed a multi-dimensional analysis with a large collection of tomato accessions. More than 13 000 triple relationships (metabolite−SNP−gene) were identified in the overlap of the mGWAS and eQTL results. The combined analysis in this work led to the identification of key determinants for metabolic diversity in the tomato but also provided novel insights into the comprehension of the effect of domestication and breeding on metabolic diversity (Zhu et al., 2018). Our understanding on the genetic bases underlying diversity of targeted traits is enhanced at a considerable larger scale using multi-dimensional analysis with metabolome data (Zhu et al., 2018), compared to that with phenotypic data (Wang et al., 2015; Wilson et al., 2015). This is beneficial from both high-throughput and accurate evaluation of metabolite contents and tremendous variation in content of a large proportion of detectable metabolites.

As a counterpart of GWAS from the lens of epigenomics, epigenome-wide association studies (EWAS) have been developed and have provided new insights to epigenetically controlled diseases in human (Rakyan et al., 2011). To explore the effects of DNA methylation on human metabolism, EWAS was conducted with DNA methylation data and metabolic data from human blood (Petersen et al., 2014). The contribution of epigenetic variation to variation in phenotypic traits has been studied with populations of epigenetic recombinant inbred lines in Arabidopsis (Johannes et al., 2009; Reinders et al., 2009). However, the important and potentially independent roles of epigenetic variants played in plant metabolic diversity remain to be illustrated, which may be an interesting topic for combined analyses of EWAS and metabolomics studies.
```

- 第二篇

```
Here, we tested the effectiveness of EMMA method by conducting the first metabolomics-based GWAS in citrus fruits. Considering the large variation in metabolism within species (Schauer et al., 2004, Bernillon et al., 2012, Wahyuni et al., 2012, Vallarino et al., 2018), we generally expect to easily identify genetic variants controlling metabolite levels. In this study, we assayed 150 biochemical compounds (55 primary metabolites and 95 lipids; Table S2-S3) in ripe fruit for a set of 194 diverse Citrus grandis accessions (Table S4; Fig. S1). Using Bonferroni correction based in the effective numbers of independent markers, we significantly detected 667 associations for a total of 14 primary metabolites including amino acids, sugars, and organic acids, and 768 association corresponding to 47 lipids (Table S5-S6 and Fig. 1; Manhattan; p ≤ XX (LOD ≥ 6.0
In general, from the perspective of genomic localization, we observed that the detected metabolite-SNP associations were spread across the genome (Fig. 1). However, for primary metabolites, a single metabolite mapped to multiple loci (ranking from 8 to 162 associations for individual primary metabolite at LOD ≥ 6.0). For sugars and organic acids, we observed cluster of associations that co-located on Chr 1, 3, and 5 as have been reported in other plant species (Lerceteau-Köhler et al., 2012; Castro, Lewers (2016). This result indicates that in these genomic regions, common genes might be involved in biosynthesis of different sugars and organic acids. Moreover, these observations can be attributed to polygenic regulation of primary metabolism rather than a few major genes as previously suggested for Arabidopsis (Wu et al., 2016) and citrus for the sugar/acid ratio (Imai et al., 2018) and also in agreement with other studies (Keurentjes et al., 2006, Chan et al., 2010). In our study, associations for lipids were also identified in several loci, however we also observed some major large-effect loci in agreement with previous studies (Chan et al., 2011, Wu et al., 2018a), indicating that the regulatory network of lipid metabolism are more linear in comparison to more complex regulation of primary metabolism.
In order to discover novel and underexplored candidate associations, we searched into the most likely candidate genes of the identified loci that were significantly associated with high LOD value based on (i) gene annotation, and (ii) prior knowledge. Thus, we focused on loci in regions showing high significant association (LOD ≥ 8.0) where one or a few candidate genes could be identified near the peak SNPs. Surprisingly, a relative lower number of significant SNPs associated to metabolites in comparison to other studies performed in other species using the same routine association mapping analysis was detected (Ruggieri et al., 2014, Wu et al., 2016, Wen et al., 2018). Here, the lower statistical power can possible due to population size and/or population structure. It is widely accepted that many false negatives for co-founded traits are correlated with population structure (Yang et al., 2013, Xing et al., 2015, Fan et al., 2006b, Mao et al., 2010). This result raises the possibility that the analyzed Citrus grandis collection presents some structural pattern that limit the potential to detect significant associations. Recently, analysis of the genome sequences of 130 accessions of different citrus species had helped to map the evolution origin and evolutionary changes in Citrus genus during domestication (Wu et al., 2018b). They found that citrus fruit crops had a complex history of admixture for which the current diversity is linked to widespread ancient introgression (Wu et al., 2018b). Interestingly, Wang et al., (2018) using deep genome-sequencing 104 citrus accessions provided concrete genetic evidence about its genetic relationships and domestication trajectories. In particular, the genetic structure of 46 mandarin wild and cultivated accessions, revealed that two Mangshan wild mandarin accessions are the wild progenitors of two independent domestication events resulting in two groups of cultivated mandarins. Interestingly, all cultivated mandarins and few wild mandarins exhibited interspecific introgression signatures from another citrus species, although the wild mandarins had purer genetic backgrounds that cultivated accessions. It is also believed that this interspecific hybridation play special roles in phenotypical diversity of this fruit, particularly fruit size and acidity (Wu et al., 2018b, Wang et al., 2018).
```

