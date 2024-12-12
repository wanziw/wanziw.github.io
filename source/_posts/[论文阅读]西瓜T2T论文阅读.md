---
title: 西瓜T2T论文阅读
date: 2024-12-10 13:04:56
categories: 论文阅读
cover: /img/cover18.jpg
tags: 
  - T2T
  - SV
  - Pangenome
description: "NG关于西瓜"
---

> - 北大现代农学研究院
>   - 22年的时候做了一篇Molecular Plant：A telomere-to-telomere gap-free reference genome of watermelon and its mutation library provide important resources for gene discovery and breeding 这里已经测了一个T2T基因组并且构建了数据库了
>   - 24年发了一篇NG
>
> 一起分析27个T2T基因组，有些模块，比如比较Detection of the centromere locations at chromosomes可能没啥参考价值，没有27个有着丝粒区域的基因组比较
>
> 但是可以参考这篇文章的多个基因组一起进行比较、建立pangenome这块
>
> 分析了SV、染色体重排
>
> 这篇的配色都挺好看的，主要研究的7个品种全文的配色统一
>
> 并且开发了数据库[WaGMDB](http://www.watermelondb.cn/#/map)

[toc]



# Abstract

- **Citrullus属**

  - 包含西瓜及其近缘的其他物种。

  - **西瓜（Citrullus lanatus）**是Citrullus属中最具经济价值和研究价值的物种。

- 研究涵盖了7个物种、27个基因型

  - 创建了一个**T2T超级Pangenomes**，扩充了原有的基因组

- 通过比较分析，发现了大量的**基因变异**和**结构变异（SVs）**，这些变异有助于理解西瓜的进化和驯化过程。

  - 这些变异解释了西瓜在驯化过程中苦味和糖分等特性的增强，以及抗病能力的降低。

# Main

西瓜虽然种植的geographical regions很多，但是 exhibit low genetic diversity。结果就是对bottleneck 阻碍了 impeding watermelon improvement

- **Citrullus属**包含**七个物种**，别的作物野生亲缘种**crop wild relatives (CWRs)**，包括：
  - Citrullus lanatus（栽培西瓜）
  - Citrullus amarus 和 Citrullus mucosospermus：半野生，主要用于食用其果肉或种子。
  - ***其他四个物种**（*C. ecirrhosus, *C. naudinianus*, *C. rehmii*, *C. colocynthis*）：具有独特的适应性特征，对基因改良和理解西瓜进化具有重要意义。
  - **地理分布**：
    - **C. amarus,** C. ecirrhosus, C. naudinianus,C. rehmii：原产于纳米布-卡拉哈里地区。
    - C. mucosospermus**：来自西非。**
    - C. colocynthis：来自北非及其他地区。
  - 育种应用**：**
    - 基因引入**：*C. colocynthis*, *C. amarus*, 和 *C. mucosospermus* 已被用于育种项目，以扩大 C. lanatus的遗传基础。**
    - 研究资源有：*C. rehmii*, *C. ecirrhosus*, *C. naudinianus*, 和 *C. lanatus subsp. cordophanus* 的研究用植物资源较少，增加这些野生种的资源有助于发现新的抗病基因、抗逆性基因及对人类健康有益的化合物基因。

- **超级泛基因组**：27个基因组，其中一个T2T基因组，涵盖所有物种，新增399.2Mb和11,225基因。
- **基因变异与结构变异**：理解西瓜进化和驯化，识别抗病和抗逆基因。
- **育种应用**：引入野生种基因，提升栽培西瓜的性状。

# Results

## T2T assemblies of 27 diverse accessions from seven species



![](https://pic.imgdb.cn/item/6757e71bd0e0a243d4e0f8e7.png)





- a、b、c是果实/种子的表型
  - a是整个水果、b是longitudinal section of fruit纵切面、c是种子
    - 27个品种包括七种西瓜物种和种间杂交种
- d图
  - 从genome-wide SNPs通过 Neighbor-joining推断出的系统发育树
  - 这里总共有**429个accessions**（**样本**），实际上自己组装的就27个品种，27个**de novo组装的accessions**用\*标识。别的402个样本是从先前研究或者别的公共数据库中获取的
  - 图注里面标识了一下后面的哪些图采用一样的**颜色编码**

- e图
  - **七组**基因组中不同转座子（TE，Transposable Elements）家族的类型及其百分比
  - **主要转座子家族**：
    - **长末端重复序列（LTR，Long Terminal Repeat）**：
      - **Gypsy**：平均占比33.45%
      - **Copia**：平均占比7.73%
    - **hAT家族**（一种多功能转座子，DNA/DTA类型）
  - **解释**：
    - **LTR转座子**在Citrullus属的基因组中占据了较高比例，尤其是Gypsy和Copia家族，这些转座子在基因组的**着丝粒区域（centromere region）**中频率较高。
    - 转座子的多样性和分布对于理解基因组结构、功能以及基因组进化具有重要意义。

- f图（这个图第一次见）
  - **使用每个26个西瓜accessions的前八个单体（monomers）构建的邻接法系统发育树**
    - monomers是指**串联重复序列的基本单位**
    - 每个基因组里面按出现频率排序的前八种串联重复序列虎v恶霸大包围u
  - **颜色编码**：不同的分支颜色表示不同的群组，树中的**四个簇（Clusters 1-4）**代表了**相似单体**的聚类
    - **四个主要簇**表明在27个样本中存在四种主要的单体类型
    - **C. colocynthis、C. rehmii和C. naudinianus**的单体在聚类中表现出独特的模式，说明这些物种在**着丝粒串联重复序列（centromeric tandem repeats）**上与其他物种存在差异。

- 组装了27个品种的T2T基因组，组装的一些不同角度的数据对比，基本上都是supplemental tables里面

> **测序技术**：
>
> **Illumina**：62×覆盖度，确认样本为二倍体，低杂合度，重复率55%。
>
> **HiFi**：799 Gb数据，81×覆盖度。
>
> **ONT超长读长**：85×覆盖度。
>
> **Hi-C**：699×覆盖度，用于contig校正和定向。
>
> **组装结果**：
>
> **27个T2T基因组**，每个基因组平均375.2 Mb。
>
> **Contig N50**：平均33.3 Mb。
>
> **共线性良好**：与G42参考基因组一致。
>
> **缺口填补**：平均每个基因组两个缺口，使用HiFi和ONT数据填补。
>
> **端粒组装**：使用七碱基重复序列CCCTAAA，提升端粒完整性。
>
> **附加基因组**：叶绿体（平均156.9 kb）和线粒体（平均622.2 kb）基因组组装完成。





## Detection of the centromere locations at chromosomes 检测染色体上的着丝粒位置

主要是分析一下27个品种的的着丝粒区域，Hi-C热图

然后根据这个分析一下不同物种的亲缘关系

主要是结合1e、1f的图分析，没啥参考价值

- **着丝粒区域**：
  - 27个样本的所有染色体上候选着丝粒区域已识别并通过Hi-C确认。

- **系统发育关系**：分别从全基因组水平上判断和着丝粒序列上判断
  - *C. naudinianus*在着丝粒序列上更接近* C. lanatus*，但全基因组水平上关系较远。*
  - C. amarus*全基因组上与* C. lanatus*更近，着丝粒序列上*C. colocynthis*与* C. lanatus*更接近。
- **转座子组成**：
  - 染色体2、3、4和6的TE组成不同，主要是LTR（Gypsy和Copia）和hAT家族。
- **串联重复序列聚类**：
  - 四个主要簇，*C. colocynthis*、*C. rehmii*和* C. naudinianus*展现出独特模式。
- **主要串联重复序列**：
  - Cluster 1为Cr2，除PKR6、PI 652554和PI 537300外在所有样本中最丰裕。
- **TE频率**：
  - LTR占56.6%，Gypsy 33.45%，Copia 7.73%。





## Watermelon super-pangenome construction and analysis

![](https://pic.imgdb.cn/item/675931dcd0e0a243d4e1b212.png)



（补充note2：除了27个基因组之外，还加入了一个原本传统的参考基因组G42。使用**Orthofinder2**工具，将来自28个接入样本的**686,583**个预测基因模型聚类成**32,513**个非冗余的泛基因家族）

构建了泛基因组pangenome：一个物种内的基因组

- **核心基因组（Core Genome）**：所有个体共有的基因。
- **可变基因组（Dispensable Genome）**：仅部分个体拥有的基因。

- 图A 
  - 横坐标是不断添加，添加28个基因组，泛基因组基因家族数目的增长趋势，最后趋于稳定closed
  - pangenome、core genome、dis genome
- 图B
  - 核心基因（core genes）：存在在**所有**基因组的基因家族中，与**基本的生物功能**相关
  - 软核心基因（softcore genes）：**大多数**基因组中，与一些**次要功能**相关，或者在某些特定条件下发挥作用。
  - 可变基因（dispensable genes）：导致不同物种或个体间表型多样化、分化的主要原因基因
  - 私有基因（private genes）：**仅存在于一个**基因组或一个物种中的基因家族
  - 四种基因在28个样本中的分布
- 图c
  - 28个样本各自的四种基因的比例
- 图d
  - presence–absence 存在-缺失景观

> 对不同类型进行了一些计算和分析
>
> **InterPro结构域注释**
>
> **基因表达水平**
>
> **核苷酸多样性（π）**，区分是否保守

## SV characterization and graph-based genome 

- Nonredundant SV 
  - 多个样本中都出现的SV只统计一次

- 图A
  - 将27个新基因组比对到G42参考基因组，将大于20 bp的SV分类为以下五类：
  - 缺失deletion
  - 插入insertion
  - 重复duplication
  - 倒位inversion
  - 易位translocation

> 验证SV识别的准确性，通过PCR扩增验证了57个平均长度为26,418 bp的大型SV，包括31个缺失和26个插入。

- 图B：

  - 通过映射所有组装变异及其与参考基因组的共线性，建立了全面的SV的landscape

  - 基于**SyRI**（Synteny and Rearrangement Identifier）生成的比较基因组可视化图，显示了27个无缺口基因组与G42参考基因组之间的同线性（synteny）和重排（rearrangements）

    - 这里是很多的基因组，要是只有一个就可以生成circos图

  - 栽培西瓜的遗传多样性较窄，而野生西瓜的遗传变异显著更大

  - **倒位“热点”**,

    - > 还识别出了倒位“热点”（见补充图8c），其中在PKR6（*C. lanatus*）接入样本的染色体11上保留了来自*C. amarus*的两个大型倒位（4.8 Mb和2.5 Mb）。
      >
      > 这些**大型倒位**已被报道能够显著**减少重组频率**，并可能导致回交育种中意外表型的连锁拖拽。

      -  **减少重组频率**：大型倒位会减少染色体上的交叉互换（crossing-over）频率，因为倒位区域的基因序列方向反转，重组时容易导致染色体配对错误。

      - **连锁拖拽**：由于倒位区域内的基因难以重组，回交育种时引入的有益基因（如抗病基因）往往会与不需要的基因一起被转移到栽培种中

  - 研究团队还在这些**大型倒位/易位区域内外**识别并注释了**相关基因**，发现这些基因主要与**纤维素合成**相关，并在特定的基因功能途径中有**显著富集**。理解SV的功能

![](https://pic.imgdb.cn/item/675aa106d0e0a243d4e2be27.png)

- 图c、d
  - 西瓜中的结构变异（SV）倾向于富集在重复DNA区域以及缺失和插入类型的区域。与大豆的研究一样
- 图e
  - 平均有27.5%的SV与基因上游或下游的2kbp区域重叠。平均有7.5%的SV导致氨基酸编码发生变化
    - 上下游2kbp可能会影响基因的调控
    - 有部分直接导致氨基酸编码变化
- 给整个物种规模的SV做了一个数据库
  - 开发了一个基于图的泛基因组的网络数据库
  - [WaGMDB](http://www.watermelondb.cn/#/map)

## Divergence among species and the origin of watermelon 

- 物种形成与染色体重排Chromosomal Rearrangements
  - 并验证了三种主要的染色体重排
  - 染色体结构的这些改变可能有助于生殖隔离，影响杂交生育能力并减少种间重组，最终导致瓜属物种的分化
  - 这从哪看出来的三个主要的染色体重排

> 在*C. colocynthis*中发现了涉及染色体1（chr01）和染色体4（chr04）的显著染色体间重排，与其他三个Citrullus物种（*C. lanatus*、*C. mucosospermus*和*C. amarus*）相比。这些染色体结构的改变可能有助于生殖隔离，影响杂交后代的生育能力，减少物种间的重组，最终导致Citrullus属物种的分化。

![](https://pic.imgdb.cn/item/675aca78d0e0a243d4e2faa5.png)



- 结合原有文献进行一些分析：为了研究不同西瓜物种中三维基因组的保守性和变异性，我们使用50 kb分辨率矩阵识别了A和B区段。结果显示，A和B区段在西瓜物种间相对保守（见补充图9a）。已有研究报道，A和B区段的变异与基因组结构变异（SVs）密切相关。在不同类型的SVs中，我们观察到一个4.5 Mb的倒位变异，导致A和B区段的变化（见补充图9b）。

- **三维基因组**指的是基因组在三维空间中的结构和组织方式，A和B区段是其重要组成部分：

  - **A区段（A Compartments）**：通常富含活跃转录的基因，代表开放的染色质区域。

  - **B区段（B Compartments）**：通常富含转录活性较低的基因，代表闭合的染色质区域。

![](https://pic.imgdb.cn/item/675ada78d0e0a243d4e2fe18.png)



## Gene gain and loss during watermelon domestication 西瓜驯化过程中的基因变化





## Contribution of SV genes during evolution and domestication 进化过程中SV基因的贡献
