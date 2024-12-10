---
title: 生信Class6 GSEA
date: 2024-12-08 16:26:54
categories: 生物信息导论实验课
cover: /img/cover7.jpg
tags:
  - GSEA
  - 富集分析
sticky: 1
description: "生物信息学导论第六节课内容 GSEA分析"
---
# GSEA

![](https://pic.imgdb.cn/item/67552be3d0e0a243d4dfded6.png)

一篇综述：[Ten Years of Pathway Analysis: Current Approaches and Outstanding Challenge](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1002375)

- 第一代：ORA 方法要求输入是差异表达基因的列表
  - 设定阈值 传统的GO/KEGG富集

- 第二代： FCS 方法使用整个数据矩阵作为输入。
  - GESA
- 第三代：除了基因组的功能注释外，基于 PT 的方法还利用基因产物之间相互作用的数量和类型
- 三种方法的目标是一样的，都是做比如pathway的富集分析

## 理论部分

GSEA论文：[Gene set enrichment analysis: A knowledge-based approach for interpreting genome-wide expression profiles](https://www.pnas.org/doi/10.1073/pnas.0506580102?url_ver=Z39.88-2003&rfr_id=ori%3Arid%3Acrossref.org&rfr_dat=cr_pub++0pubmed)

GSEA官网：[GSEA](https://www.gsea-msigdb.org/gsea/index.jsp)

- **定义**： 基因集富集分析(Gene Set Enrichment Analysis, GSEA)是一种计算方法，用来确定一组先验定义的基因集是否**在两种生物状态**之间显示出统计学上显著的、一致的差异。

- **基本原理**： 使用预定义的基因集（通常来自功能注释或先前实验的结果），将基因按照在两类样本中的差异表达程度排序，然后检验预先设定的基因集合是否在这个排序表的顶端或者底端富集。基因集合富集分析检测基因集合而不是单个基因的表达变化，因此可以包含这些细微的表达变化，预期得到更为理想的结果
  - 两个不同条件下筛选出一些差异表达的基因，是没有什么意义的。相反，我们可以将这些基因**按其相关的生物过程或通路**进行分组，这样可以简化分析的复杂性。通过使用现有的**知识库**（比如GO/KEGG/MSigDB），研究人员能够识别出在特定通路中起作用的基因和蛋白质。这不仅将成千上万的基因缩减到几百个通路，使得实验分析更加高效，还能更清晰地解释不同条件下活跃的生物通路，从而提供比单纯列出差异基因更有价值的见解。

- 基因集富集分析（Gene set enrichment analysis,GSEA）方法无需预先设定显著差异基因，其对差异不显著但具有重要功能的基因具有独特优势
  - GSEA需要表达量的数据，GO/KEGG不需要

> 这与之前讲述的GO/KEGG富集分析不同。GO/KEGG富集分析是先筛选差异基因，再判断差异基因在哪些注释的通路存在富集；这涉及到阈值的设定，存在一定主观性并且只能用于表达变化较大的基因，即我们定义的显著差异基因。而GSEA则不局限于差异基因，从基因集的富集角度出发，理论上更容易囊括细微但协调性的变化对生物通路的影响，尤其是差异倍数不太大的基因集

![](https://pic.imgdb.cn/item/6755252ed0e0a243d4dfdd79.png)

- 工作流程介绍

> 基因集定义：首先，**GSEA需要一个事先定义好的基因集合，这些基因通常按照其在特定生物学通路、功能类别或疾病过程中的作用进行组织**。这些基因集可以来自公共数据库，如Gene Ontology、KEGG Pathway、Reactome，或者是研究者自己根据文献和领域知识构建的。
>
> 基因表达数据：GSEA需要分析的基因表达数据，通常是从微阵列或RNA测序实验中获得的。这些数据包括不同条件或样本中基因的表达水平。
>
> 排列(permutation)检验：GSEA的核心思想是通过对基因集的成员在整个基因表达数据中的排列来确定它们的富集程度。具体来说，GSEA将所有基因根据其在不同条件下的表达水平进行排序。然后，它从基因集的一端开始，计算该基因集中的基因在排序列表中的偏离程度。如果基因集中的基因在排序列表的某个位置中集中排列，说明该基因集富集在特定的生物学过程或通路中。这个过程通过构建一个富集分数（Enrichment Score）来量化。
>
> 统计显著性：对于每个基因集，GSEA 计算一个富集分数，并基于随机排列检验来估计其统计显著性。如果一个基因集的富集分数在随机排列中的分布表现出显著差异，那么就认为这个基因集在样本中富集。
>
> 结果可视化：最后，GSEA 会生成结果报告，其中包括富集分数、基因集的统计显著性以及相关通路或功能的信息。这些结果可视化为富集图谱，用于展示不同基因集的富集情况。

- 基本概念

  - ES（Enrichment Score）：富集得分 
    - ES反应基因集成员s在排序列表L的两端富集的程度。
    - 计算方式是：从基因集L的第一个基因开始，计算一个累计统计值。当遇到一个落在s里面的基因，则增加统计值。遇到一个不在s里面的基因，则降低统计值。 每一步统计值增加或减少的幅度与基因的**表达变化程度**（fold-change值）是相关的。
    - 富集得分ES最后定义为最大的峰值。正值ES表示基因集在列表的顶部富集，负值ES表示基因集在列表的底部富集
    - **p-value**用来评估富集得分(ES)的显著性，通过排列检验 (permutation test)计算观察到的富集得分(ES)出现的可能性。
  - NES (Normalized Enrichment Score)：标准化富集得分 
    - 每个基因子集s计算得到的ES根据基因集的大小进行标准化得到标准化富集得分Normalized Enrichment Score (NES)。
    - 随后会针对NES计算假阳性率FDR（**在所有被判定为阳性/显著的结果中，实际上是错误（假阳性）的比例**。）。
  - Leading-edge subset：
    - 并不是所有的基因集的所有成员通常都会参与生物过程
    - 领头基因亚集 对富集贡献最大的基因成员

- 一般认为|NES|>1，p-value<0.05，FDR<0.25的通路是显著富集的。 

  

## 实战部分

- 安装gseapy包,python中用来做GSEA分析的第三方库

> [GSEApy-github](https://github.com/zqfang/GSEApy)
>
> [GSEAPY官方文档](https://gseapy.readthedocs.io/en/latest/introduction.html)

```python
# 使用 conda 安装（仅限 MacOS_x86-64 和 Linux）
conda install -c bioconda gseapy
 
# 使用 pip 安装
pip install gseapy
```

> 给大家准备了两个ipynb文件和两份数据
>
> 其中 GSEA_in_python.ipynb 对应的是'DE_results.csv'数据
>
> GESA_analysis.ipynb对应的是'PRMT5_DMSO_differential.txt'数据
>
> 因为数据里面有些列名的不同，所以准备了两个，本质上是一样的东西，代码脚本中可能有些变量名命名的不太一样。
>
> 上课我们讲的是GESA_analysis.ipynb

### 数据集结构

差异表达基因

里面有1118个基因

设计的两个实验条件

1. **PRMT5**：涉及PRMT5（蛋白精氨酸甲基转移酶5）的处理条件。
2. **DMSO**：使用DMSO（二甲基亚砜）作为对照处理条件，DMSO通常作为溶剂对照。

![](https://pic.imgdb.cn/item/67553c25d0e0a243d4dfe234.png)

- 这里的参数不重要，只要有基因标识和用来排序的数据就行（gene-level statistics）

| Gene         | 表示基因名称或标识符。                                       | FDR(+)          | 正效应方向的假发现率。             |
| ------------ | ------------------------------------------------------------ | --------------- | ---------------------------------- |
| Category     | 指定基因的分类或功能类别。                                   | P(+)            | 正效应方向的p值。                  |
| PRMT5_biased | 表示与PRMT5相关的基因偏向性。                                | FDR(replicates) | 基于重复实验的假发现率。           |
| DMSO_biased  | 表示与DMSO相关的基因偏向性。                                 | P(replicates)   | 基于重复实验的p值。                |
| PRMT5        | PRMT5条件下的值，例如表达量或信号强度。                      | P(sgRNAs)       | 基于sgRNA结果的p值。               |
| DMSO         | DMSO条件下的值，例如表达量或信号强度。                       | FDR(sgRNAs)     | 基于sgRNA结果的假发现率。          |
| Z            | Z分数，表示标准化的效应值。Z值表示某个基因的表达差异与总体数据的平均差异相比，有多少个标准差。换句话说，Z值告诉我们一个基因的变化有多异常或显著。 | FDR(-)          | 负效应方向的假发现率。             |
| P(-)         | 负效应方向的p值。                                            | Rank            | 基因在特定指标或综合结果下的排名。 |

### 排序

Z值用来排序

```python
df['Rank'] = df.Z

df.sort_values(by='Rank',inplace=True)
```

- 查看gene和rank两列

![](https://pic.imgdb.cn/item/67553cd4d0e0a243d4dfe28b.png)

至此完成了基本的预处理，也就是得到了后续分析的输入

### GSEA分析

GSEA（Gene Set Enrichment Analysis，基因集富集分析）

gseapy这个包已经有了一些library

```python
gp.get_library_name()
```

> 用于基因集富集分析（GSEA）的库（libraries）。这些库通常包含特定的基因集、路径（pathways）、基因-疾病关联等信息，用于帮助研究人员从大量基因数据中识别出具有生物学意义的模式。挑几个看看：
>
> **1. KEGG_2021_Human**
>
> **来源**：**KEGG（Kyoto Encyclopedia of Genes and Genomes）**
>
> **内容**：KEGG 是一个综合性的数据库，包含了大量的生物路径（**pathways**）、疾病信息、药物信息等。KEGG_2021_Human 特指2021年版本的人类KEGG路径集。
>
> **作用**：用于识别和分析基因在已知生物路径中的富集情况，帮助理解基因在细胞过程、信号传导、代谢途径等中的作用。
>
> **2. GO_Biological_Process_2021**
>
> **来源**：**Gene Ontology（GO）**
>
> **内容**：GO 提供了一套统一的术语来描述基因和基因产物的功能，分为三个主要类别：生物过程（Biological Process）、分子功能（Molecular Function）和细胞组分（Cellular Component）。GO_Biological_Process_2021 指的是2021年版本的生物过程类基因集。
>
> **作用**：用于分析基因在不同生物过程中（如细胞周期、信号传导、代谢过程等）的富集情况，帮助揭示基因在特定生物学功能中的角色。
>
> **3. ChEA_2015**
>
> **来源**：**ChEA（ChIP-X Enrichment Analysis）**
>
> **内容**：ChEA 包含了大量的转录因子（Transcription Factors, TFs）与其靶基因的关联信息，基于ChIP-seq等实验数据构建。
>
> **作用**：用于识别和分析基因在特定转录因子调控下的富集情况，帮助理解基因调控网络和转录因子的作用。
>
> **4. Human_Phenotype_Ontology**
>
> **来源**：**Human Phenotype Ontology（HPO）**
>
> **内容**：HPO 提供了对人类疾病和表型特征的标准化描述，涵盖了各种临床表型和疾病特征。
>
> **作用**：用于分析基因与特定人类表型或疾病特征的关联情况，帮助在基因表达数据中识别与临床表型相关的基因集。

- ger the GESA results
  - 参数rnk：传入dataframe类型，包含基因及其对应的排名分数。通常，这个分数基于基因在不同条件下的表达差异（如log2 fold change）。预排序GSEA需要一个排序好的基因列表，df_rank就是这个排序好的基因列表。
  - 参数gene_sets：用于富集分析的基因集，可以选择GO啊或者KEGG啊。可以从前面的library_name中寻找到
  - 执行gp里的prerank方法进行分析，结果存储在变量gsea_res中

```python
gsea_res = gp.prerank(rnk = df_rank, gene_sets='GO_Biological_Process_2021', seed = 1024)
```

- 先简单查看一下结果

```python
## The results of GSEA stores as a dictionary

print(list(gsea_res.results.keys())[0])

print(list(gsea_res.results.values())[0])
```

结果展示一部分,这里的第一个并不代表是最富集的，因为还要看fdr和pvalue

```
regulation of cellular localization (GO:0060341)
{'name': 'prerank', 'es': -0.6650458489873552, 'nes': -1.0809540343472221, 'pval': 0.4166666666666667, 'fdr': 0.6882871982831866, 'fwerp': 1.0, 'tag %': '4/35', 'gene %': '6.83%', 'lead_genes': 'SPAG5;PARP1;KDM1A;HSP90AA1', 'matched_genes': 'LYN;WWC1;REEP6;PINK1;GSN;STXBP2;PARD6G;REEP5;LRP5;NR1D1;TRIM46;LRRK2;CAMK2D;BRSK1;DVL3;DYNC1H1;MAP2;KIAA1614;GOSR1;NUMA1;FER;CSNK1E;PPM1F;TTL;FES;CDK16;STXBP4;EFNA5;DVL1;EPHA5;HSP90AB1;HSP90AA1;KDM1A;PARP1;SPAG5', 'hits': [401, 530, 717, 1233, 1242, 1304, 1421, 1947, 1982, 1998, 2091, 2165, 2749, 2945, 3506, 3850, 4853, 5226, 5445, 5656, 6508, 6521, 6625, 7374, 7792, 7853, 8143, 8276, 8307, 8467, 9270, 10076, 10089, 10503, 10771], 'RES':
```

> - **Term**：gene set基因集名称（如GO生物过程中的某个特定过程）
>   - **library中的一条，基因集就是term**
>   - regulation of cellular localization (GO:0060341):进行富集分析的特定基因集名称，属于Gene Ontology（GO）中的一个生物过程类别
> - **fdr**：错误发现率，表示该基因集富集结果的显著性。fdr值越小，越显著。
>   - 多重检验校正。**最重要的参数之一**。通常，fdr < 0.05 被认为是显著的富集结果，表示结果可靠性高
> - **es**：富集得分，表示基因集在基因列表中的富集程度。
>   - 衡量该基因集在基因排序列表中的富集程度。正值表示基因集在列表顶部（上调基因）富集，负值表示在列表底部（下调基因）富集。
> - **pval**
>   - p值越小，结果越显著
> - **nes**：标准化**Normalized**的富集得分，方便不同基因集之间的比较。
> - **lead_genes（关键基因）**
>   - SPAG5;PARP1;KDM1A;HSP90AA1
>   - 该基因集富集的关键基因、帮助识别哪些基因在富集中起主要作用
> - **hits（命中位置）**
>   - 数字表示匹配基因在基因排序列表中的具体位置

```python
# 提取结果转换成dataframe
out_list = []

for term in gsea_res.results:
    p = gsea_res.results[term]['pval']
    fdr = gsea_res.results[term]['fdr']
    nes = gsea_res.results[term]['nes']
    es = gsea_res.results[term]['es']
    gene = gsea_res.results[term]['lead_genes']
    out_list.append([term, p, fdr, nes, es, gene])

df_out = pd.DataFrame(out_list, columns = ['Term','p_value','fdr', 'nes', 'es','gene']).sort_values('fdr').reset_index(drop = True)
df_out
```

![](https://pic.imgdb.cn/item/67553f08d0e0a243d4dfe31a.png)



### 画图

参考官方文档的画图部分

https://gseapy.readthedocs.io/en/latest/gseapy_example.html#Prerank-example

有单个term展现的、多个term同时展现、气泡图

- 单个
  - 第一种是简单的方法，快速展现
  - 第二种是可以更加灵活调节的方法

```python
from gseapy.plot import gseaplot
# 方法1
# terms = gsea_res.res2d.Term
# axs = gsea_res.plot(terms=terms[1])
# 方法2
term_to_plot = df_out['Term'][0]
gseaplot(rank_metric=gsea_res.ranking, term=term_to_plot, **gsea_res.results[term_to_plot])
```

- 多个term

```
terms = gsea_res.res2d.Term
axs = gsea_res.plot(terms=terms[1:5],
                   # legend_kws={'loc': (1.2, 0)}, # set the legend loc
                   show_ranking=True, # whether to show the second yaxis
                   figsize=(3,4)
                  )
```

- 气泡图展示富集的通路

```python
from gseapy import dotplot
# to save your figure, make sure that ``ofname`` is not None
ax = dotplot(gsea_res.res2d,
             column="FDR q-val",
             title='GO_Biological_Process_2021',
             cmap=plt.cm.viridis,
             size=6, # adjust dot size
             figsize=(4,5), cutoff=0.5, show_ring=False)
```





# GO富集

[geneontology](https://geneontology.org/)





