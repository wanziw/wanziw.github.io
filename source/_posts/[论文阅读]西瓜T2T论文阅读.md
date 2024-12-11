---
title: 西瓜T2T论文阅读
date: 2024-12-10 13:04:56
categories: 论文阅读
cover: /img/cover18.jpg
tags: 
  - T2T
  - SV
description: "NG关于西瓜"
---

> 一起分析27个T2T基因组，有些模块，比如比较Detection of the centromere locations at chromosomes没啥参考价值，没有27个有着丝粒区域的基因组比较

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
  - 横坐标是不断添加
  - closed



## SV characterization and graph-based genome



