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
> 使用**syri**软件分析了SV、染色体重排
>
> 这篇的配色都挺好看的，主要研究的7个品种全文的配色统一
>
> 并且开发了数据库[WaGMDB](http://www.watermelondb.cn/#/map)

[toc]



# Abstract



> 根据429分材料的系统发育关系和地理分布，选择了27个具有代表性的种质，均组装至T2T水平，并与一个现有的T2T基因组共同构建了西瓜的属级超级泛基因组。SV对基因组多态性和功能基因变异的影响大于SNP，将27个新基因组与G42参考基因组（也是一种栽培西瓜）比对，共鉴定了461,987个非冗余SV。西瓜的SVs倾向于富集在DNA重复区域和缺失与插入，平均27.5%的SVs与基因上游或下游2 kbp区域重叠，平均7.5%的SVs引起了氨基酸编码的变化，这可能会导致基因功能的多样性。这些结果表明，超级泛基因组中的SVs反映了栽培西瓜及其相关物种进化过程中发生的巨大结构变化，加深了对西瓜属进化的基因组和表型变化的认识。

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

7个species 里面27个品种

> - *Citrullus lanatus*  种植最广泛的西瓜
>
> - **野生近缘种（CWRs）** ：
>   - 半野生：*Citrullus amarus*、*Citrullus mucosospermus*
>   - 完全野生（资源较少）：*Citrullus ecirrhosus*、*Citrullus naudinianus*、*Citrullus rehmii* 和 Citrullus colocynthis
>
> 还有一个栽培西瓜的亚种被认为(*Citrullus lanatus* subsp. *cordophanus*) 被认为是栽培西瓜的可能祖先，来自苏丹东北非地区。

- 研究大概的目的
  - 利用这些野生近缘种，可以拓宽栽培西瓜的遗传基础，发现与抗病性、抗逆性以及促进人类健康的化合物（如苦瓜甙和瓜氨酸）相关的新等位基因。
  - 构建属级超级泛基因组（super-pangenome）有助于识别和利用这些野生种中的遗传多样性，推动栽培西瓜的基因改良和进化研究。

| Entry# | Accession        | Taxonomy            |                                 |
| ------ | ---------------- | ------------------- | ------------------------------- |
| 1      | PI 596694 (male) | C. naudinianus      |                                 |
| 2      | PI 525081        | C. colocynthis      |                                 |
| 3      | PI 632755        | C. colocynthis      |                                 |
| 4      | PI 652554        | C. colocynthis      |                                 |
| 5      | PI 537300        | C. colocynthis      |                                 |
| 6      | PI 670011        | C. rehmii           |                                 |
| 7      | PI 673135        | C. ecirrhosus       |                                 |
| 8      | PI 482276        | C. amarus           |                                 |
| 9      | PI 296341-FR     | C. amarus           | 分析栽培过程中基因变化用到      |
| 10     | PI 271769        | C. amarus           |                                 |
| 11     | PI 189225        | C. amarus           |                                 |
| 12     | RCAT 055816      | C. amarus           |                                 |
| 13     | PI 532732        | C. mucosospermus    |                                 |
| 14     | PI 595203        | C. mucosospermus    | 分析栽培过程中基因变化用到      |
| 15     | PI 254622        | C. lanatus landrace |                                 |
| 16     | HeiShanRen       | C. lanatus landrace |                                 |
| 17     | PI 381740        | C. lanatus landrace |                                 |
| 18     | DaBanHongZiGua   | C. lanatus landrace |                                 |
| 19     | PI 288522        | C. lanatus landrace |                                 |
| 20     | SanBaiGua        | C. lanatus landrace |                                 |
| 21     | ShiHong No.2     | C. lanatus cultivar |                                 |
| 22     | Sugarlee         | C. lanatus cultivar |                                 |
| 23     | Charleston Gray  | C. lanatus cultivar |                                 |
| 24     | Calhoun Gray     | C. lanatus cultivar |                                 |
| 25     | Allsugar         | C. lanatus cultivar |                                 |
| 26     | **G42**          | C. lanatus cultivar | 这篇T2T构建之前的主要参考基因组 |
| 27     | **PKR6**         | C. lanatus cultivar | 分析栽培过程中基因变化用到      |

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

### 品种间的差异

染色体重排对物种形成很关键

- 物种形成与染色体重排Chromosomal Rearrangements
  - 并验证了三种主要的染色体重排
  
  - 染色体结构的这些改变可能有助于生殖隔离，影响杂交生育能力并减少种间重组，最终导致瓜属物种的分化
  
  - 这从哪看出来的三个主要的染色体重排：
  
    - 下面7个品种染色体按照1-11从左到右进行排序的
  
    - **彩色的线是gene block 一般是多个基因组成的共线性区域**
  
      

> 在*C. colocynthis*中发现了涉及染色体1（chr01）和染色体4（chr04）的显著染色体间重排，与其他三个Citrullus物种（*C. lanatus*、*C. mucosospermus*和*C. amarus*）相比。这些染色体结构的改变可能有助于生殖隔离，影响杂交后代的生育能力，减少物种间的重组，最终导致Citrullus属物种的分化。

![](https://pic.imgdb.cn/item/675d3b35d0e0a243d4e3dbff.png)



- 结合原有文献进行一些分析：为了研究不同西瓜物种中三维基因组的保守性和变异性，我们使用50 kb分辨率矩阵识别了A和B区段。结果显示，A和B区段在西瓜物种间相对保守（见补充图9a）。已有研究报道，A和B区段的变异与基因组结构变异（SVs）密切相关。在不同类型的SVs中，我们观察到一个4.5 Mb的倒位变异，导致A和B区段的变化（见补充图9b）。

>  **三维基因组**指的是基因组在三维空间中的结构和组织方式，A和B区段是其重要组成部分：
>
> - **A区段（A Compartments）**：通常富含活跃转录的基因，代表开放的染色质区域。
>
> - **B区段（B Compartments）**：通常富含转录活性较低的基因，代表闭合的染色质区域。
>
>
> 使用PCA做一下大部分A/B compartments 是保守的，说明这表明这些基因组区域的三维结构变化不大，是同个祖先。
>
> 然后发现一些结构变异（如染色体倒位）会导致局部A/B compartments 的变化。比如chr11上的4.5 Mb倒位使得A和B compartments 在倒位区域内发生了切换，这可能会导致基因表达模式的改变。



![](https://pic.imgdb.cn/item/675ada78d0e0a243d4e2fe18.png)

### 栽培种西瓜的祖先

- 以前的报告说*C. lanatus* subsp. *cordophanus*这个亚种可能是栽培西瓜的祖先
  - 接下来的内容都是在证明除了cordophanus可能是祖先之外，*C. mucosospermus*这个野生种也有可能是栽培种西瓜的祖先
- 通过图3a可以看出野生西瓜 （*C. amarus*） 和栽培西瓜 （*C. lanatus*） 之间的 SV 呈爆炸性增加。但是其中*C. mucosospermus*这个野生西瓜跟 lanatus栽培西瓜之间SV没有太明显的差异

![](https://pic.imgdb.cn/item/675d3b52d0e0a243d4e3dc07.png)

- 图C，维恩图，栽培西瓜 （*C. lanatus*）中识别出了362个SVs
  - 33个来自C. mucosospermus
  - 68个来自于亚种cordophanus
  - 200个SVs在C. mucosospermus和cordophanus中共有
- 图D：这里列举了三个特定基因的SVs
  - **ClG42_07g0080600**：通过选择性扫荡（selective sweeps）识别出来，表明该基因区域在驯化过程中经历了强烈的选择压力。
  - **ClG42_01g0030700**：与果实大小相关的数量性状基因座（QTLs）有关，意味着该基因的变异可能影响西瓜果实的尺寸。
  - **ClG42_03g0058200**：与种子外壳颜色相关的QTLs有关，表明该基因的变异可能影响西瓜种子的颜色。
  - 其中*C. lanatus*（G42） 和 *C. mucosospermus* 具有相同的单倍型，与之前研究中的*C. lanatus* 亚种 *cordophanus*不同。**说明了*C. mucosospermus* 也有可能是*C. lanatus*的祖先，而不仅仅是之前研究中的cordophanus就是祖先了**
- 图e：进一步展示了基因组中的Large inversion倒置，包括*C. lanatus*和可能的两个祖先
  - 除了都inherit的inversion，单独把inherit自cordophanus用紫框框出来，把C.mucosospermus用黄框框出来，可以看出黄框的挺多
  - 然后补充的表20里面通过实验手段对检测到的倒位（Inversion）进行了验证
  - 结合补充图10（对表20的可视化，Sanger sequencing validation of inversions listed in Table S20）
  - 图11一些特定基因的SNPs（SNP的分布模式可以揭示不同西瓜品种的进化历史和适应性特征）
  - 进一步证明了*C. mucosospermus*也有可能是祖先

## Gene gain and loss during watermelon domestication 西瓜驯化过程中的基因变化



- 西瓜在培育育种、domestication的过程中，基因有gain也有loss。
  - 会影响disease resistance, sugar accumulation and fruit flesh coloration（果肉着色）这些性状

![](https://pic.imgdb.cn/item/675d53cdd0e0a243d4e3f535.png)

> **Cucurbit 科**：包括西瓜（*Citrullus* 属）、黄瓜（*Cucumis* 属）、甜瓜（*Cucumis melo*）、南瓜（*Cucurbita* 属）等多个属。

- 系统发育树
  - 比较分析single-copy orthologous genes（但不同物种之间只存在一个的拷贝同源基因） 构建了*Citrullus*和相关的cucurbit物种之间的系统发育树
  - 发现了最近的分化事件是*C. lanatus* 和 *C. mucosospermus*
    - 进一步论证了上一part的观点
  - 进化的过程中基因家族的丢失大于获得的基因
- 然后给了一个抗病Lox基因的分布

![](https://pic.imgdb.cn/item/675d622fd0e0a243d4e3fcf6.png)

分析了PKR6（一个近交系的栽培西瓜，其多种疾病抗性是通过不同种间杂交积累而成的）

- C：基因组信息
  - 浅蓝色区域表示来自 PI 296341-FR (*C. amarus*)的纯合片段，紫色区域表示来自 PI 595203 (C. mucosospermus)的纯合片段，深蓝色表示与两个种质一致的区域
    - 大部分是跟PI 296341-FR 颜色一样
  - （**不知道咋根据图C鉴定出来的**）鉴定出了一个QTL叫做*Qfon1.1*，对于Fon race 1有良好的抗性
    - 通过与G42基因组（易感）比对，QTL缩小到364 kb区域，**缩小之后更好鉴定是什么基因**
- D：展示了G42、PI 296341-FR 和 PKR6被Fon race 2感染的表型
  - 说明G42易于感染，但是同样作为栽培种的 PKR6不容易被感染，然后野生种PI 296341-FR也不会被感染
  - PKR6比CWRs野生种更适合作为改良的选择
  - 补充表15检测到了PKR6chr11上面来自的**连锁拖拽序列**，说明利用当前的基因组信息，可以将丢失的抗性基因有目的地整合到精英细胞系中。
- 未来的工作可能集中在别的野生种（ *C. naudinianus*、*C. ecirrhosus* 和 *C. rehmii* ）的抗性基因渗入优良西瓜系。

![](https://pic.imgdb.cn/item/675d678fd0e0a243d4e3fdbe.png)

cultivated watermelon 栽培种主要是改变了sweetness甜度和flesh color果肉的颜色

- 图e flesh color的GWAS
  - LCYB的碱基变化导致西瓜的果肉颜色变化

> landrace: *landrace地方品种，相对于育成品种和野生资源而言*。在19世纪系统育种以前世界上种植的都是landrace。

图f、g就是比较了40多个品种的这个表型，并且每个品种都标注了LCYB的SNP是什么（第一个SNP是G/T、第二个SNP是G/A）还有TST2是1copy还是2copy，然后画了统计图

- 图f 
  - brix是糖的浓度 比较了brix跟 *TST2*基因 表达和 *TST2* 基因的CNV（1copy和2copy）的比较
  - 发现*TST2* 基因的扩增导致糖分的增加

- 图g
  - 发现了（*TST2*  2copy与 *LCYB-GG*）和（*TST2* 1copy与 *LCYB-TA*）有很强的相关性，说明这两个基因是同时在驯化的
- 简单还讲了一下T2T2基因拷贝数的变异导致果肉和糖分变化的相关蛋白和通路

> 研究还发现，**色素体磷酸转运蛋白ClPHT4;*TST2*中的2**（ClG42_10g0214700）的高水平表达对于果肉颜色的形成是必需的。在栽培西瓜中，糖和植物激素信号传导途径的独特模型调控了 **ClPHT4;2** 的转录，与野生种相比表现出明显不同。这表明，**TST2基因的拷贝数** 可能通过调节糖信号通路，进而影响 **ClPHT4;2** 的表达，促进了西瓜糖分积累和果肉颜色的共同选择。



总结：重新引入丢失的抗性基因并了解糖积累和果肉着色的共同进化对于有效的西瓜育种计划至关重要。





## Contribution of SV genes during evolution and domestication 进化过程中SV基因的贡献

多个表型：bitterness, sugar content, flesh color, shape, ripening成熟度 and seed size

为了探讨与这些性状相关的基因是否受到环境选择和/或人为选择的影响

1.  扫描了*C. colocynthis*、*C. amarus*、*C. mucosospermus* 和 *C. lanatus* 的**启动子和 CDS**（Coding Sequence，编码序列） 中的 **SVs**

> 通过比较野生西瓜和栽培西瓜，进行了选择性扫荡（selective sweeps）分析，可能影响性状多样性的携带SVs的新候选基因
>
> - 选择性扫荡：
>   - **基因扫描**：通过比较野生西瓜和栽培西瓜，识别出在选择性扫荡过程中受到选择的基因。
>   - **候选基因识别**：在1,750个通过选择性扫荡检测到的基因中，有79个基因的编码区存在SVs（详见补充表28）。
>   - **功能注释**：利用Swiss-Prot数据库和转录组数据分析，进一步筛选出可能与其他重要功能相关的候选基因（详见补充表29）。



![](https://pic.imgdb.cn/item/675d70fbd0e0a243d4e3fef2.png)

- 图左边
  - 扫描之后的结果发现，这些功能基因的SV主要是存在在*C. colocynthis* 和 *C. amarus* 中，而不在*C. mucosospermus* 和 *C. lanatus*中，说明驯化的过程被淘汰了，一般是位于其实密码子的上游、少数在编码区

- 图右边，不同性状相关的基因在不同品种的果实和叶子里面的表达量大小
  - 与果实甜味、苦味和果色相关的基因的 SVs 与不同种质果实中的表达模式一致
- 进一步进行了分析苦味的丧失
  - **西瓜果实的一个关键驯化特征是苦味的丧失 具体进行了原因分析，比如相关的化合物、其合成与什么调节因子（基因）有关，这个基因在不同品种间的表达量怎么样，是什么原因导致的这个表达量的变化，是否跟SV相关**

- 分析了糖和色素积累相关的化合物

- 讲了一下果形、种子大小和果实成熟度在不同物种间表现出多样性

> 与苦味、糖含量和果肉颜色在驯化过程中呈现出下降或上升趋势不同，果形、种子大小和果实成熟度在不同物种间表现出多样性。在驯化过程中，果形由小变大后又略微变小，种子大小也存在变化。虽然已有研究表明基因表达模式与果形和种子大小性状相关，但这些表达模式与结构变异（SV）的出现并不一致。与果实成熟相关的两个基因在*C. colocynthis*和*C. amarus*中存在结构变异，但这些变异在四个物种中的基因表达并不一致。驯化过程复杂，结构变异只是影响*Citrullus*属物种间性状变异的众多因素之一。

# Methods和peer review

