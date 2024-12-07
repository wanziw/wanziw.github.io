---
title: 生信Class6 numpy/pandas/KEGG
date: 2024-12-02 16:57:33
categories: 生物信息导论实验课
cover: /img/cover16.jpg
tags:
  - numpy
  - pandas
sticky: 1
description: "生物信息学导论第六节课基本内容 numpy和pandas的基本使用 以及一些案例"
---

[toc]



# Numpy 和pandas使用

## 创建conda环境

- 在终端中创建一个python环境
  - 名字为bioinformatics，可以替换为自己喜欢的别的名字，一般是根据项目来
  - 版本为3.11，别的版本当然也行

```bash
conda create --name bioinformatics python=3.11
```

- 大家上次创建过一个环境的话，就用那个就行，忘记名字的可以通过这个命令查已有的conda环境

```bash
conda env list
```

- 激活环境

```bash
conda activate bioinformatics
```

- 下载包

```python
pip install numpy
pip install pandas
```

- 下载慢的可以添加镜像

```python
pip install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install pandas -i https://pypi.tuna.tsinghua.edu.cn/simple
```

- pycharm里添加上这个环境

## 初识numpy pandas等第三方库

### NumPy

NumPy（Numerical Python的简称）是Python科学计算的基础包。本书大部分内容都基于NumPy以及构建于其上的库。它提供了以下功能（不限于此）：

- 快速高效的多维数组对象ndarray。

- 用于对数组执行元素级计算以及直接对数组执行数学运算的函数。

- 用于读写硬盘上基于数组的数据集的工具。

- 线性代数运算、傅里叶变换，以及随机数生成。

  -成熟的C API， 用于Python插件和原生C、C++、Fortran代码访问NumPy的数据结构和计算工具。

除了为Python提供快速的数组处理能力，NumPy在数据分析方面还有另外一个主要作用，即作为在算法和库之间传递数据的容器。对于数值型数据，NumPy数组在存储和处理数据时要比内置的Python数据结构高效得多。此外，由低级语言（比如C和Fortran）编写的库可以直接操作NumPy数组中的数据，无需进行任何数据复制工作。因此，许多Python的数值计算工具要么使用NumPy数组作为主要的数据结构，要么可以与NumPy进行无缝交互操作。

### pandas



pandas提供了快速便捷处理结构化数据的大量数据结构和函数。自从2010年出现以来，它助使Python成为强大而高效的数据分析环境。本书用得最多的pandas对象是DataFrame，它是一个面向列（column-oriented）的二维表结构，另一个是Series，一个一维的标签化数组对象。

pandas兼具NumPy高性能的数组计算功能以及电子表格和关系型数据库（如SQL）灵活的数据处理功能。它提供了复杂精细的索引功能，能更加便捷地完成重塑、切片和切块、聚合以及选取数据子集等操作。因为数据操作、准备、清洗是数据分析最重要的技能，pandas是本书的重点。

作为背景，我是在2008年初开始开发pandas的，那时我任职于AQR Capital Management，一家量化投资管理公司，我有许多工作需求都不能用任何单一的工具解决：

- 有标签轴的数据结构，支持自动或清晰的数据对齐。这可以防止由于数据不对齐，或处理来源不同的索引不同的数据，所造成的错误。
- 集成时间序列功能。
- 相同的数据结构用于处理时间序列数据和非时间序列数据。
- 保存元数据的算术运算和压缩。
- 灵活处理缺失数据。
- 合并和其它流行数据库（例如基于SQL的数据库）的关系操作。

我想只用一种工具就实现所有功能，并使用通用软件开发语言。Python是一个不错的候选语言，但是此时没有集成的数据结构和工具来实现。我一开始就是想把pandas设计为一款适用于金融和商业分析的工具，pandas专注于深度时间序列功能和工具，适用于时间索引化的数据。

对于使用R语言进行统计计算的用户，肯定不会对DataFrame这个名字感到陌生，因为它源自于R的data.frame对象。但与Python不同，data frames是构建于R和它的标准库。因此，pandas的许多功能不属于R或它的扩展包。

pandas这个名字源于panel data（面板数据，这是多维结构化数据集在计量经济学中的术语）以及Python data analysis（Python数据分析）。

### matplotlib



matplotlib是最流行的用于绘制图表和其它二维数据可视化的Python库。它最初由John D.Hunter（JDH）创建，目前由一个庞大的开发团队维护。它非常适合创建出版物上用的图表。虽然还有其它的Python可视化库，matplotlib却是使用最广泛的，并且它和其它生态工具配合也非常完美。我认为，可以使用它作为默认的可视化工具。

### IPython和Jupyter

IPython项目起初是Fernando Pérez在2001年的一个用以加强和Python交互的子项目。在随后的16年中，它成为了Python数据栈最重要的工具之一。虽然IPython本身没有提供计算和数据分析的工具，它却可以大大提高交互式计算和软件开发的生产率。IPython鼓励“执行-探索”的工作流，区别于其它编程软件的“编辑-编译-运行”的工作流。它还可以方便地访问系统的shell和文件系统。因为大部分的数据分析代码包括探索、试错和重复，IPython可以使工作更快。

2014年，Fernando和IPython团队宣布了Jupyter项目，一个更宽泛的多语言交互计算工具的计划。IPython web notebook变成了Jupyter notebook，现在支持40种编程语言。IPython现在可以作为Jupyter使用Python的内核（一种编程语言模式）。

IPython变成了Jupyter庞大开源项目（一个交互和探索式计算的高效环境）中的一个组件。它最老也是最简单的模式，现在是一个用于编写、测试、调试Python代码的强化shell。你还可以使用通过Jupyter Notebook，一个支持多种语言的交互式网络代码“笔记本”，来使用IPython。IPython shell 和Jupyter notebooks特别适合进行数据探索和可视化。

Jupyter notebooks还可以编写Markdown和HTML内容，它提供了一种创建代码和文本的富文本方法。其它编程语言也在Jupyter中植入了内核，好让在Jupyter中可以使用Python以外的语言。







## 使用jupyter 

激活环境，下载jupyter 

> Jupyter Notebook（此前被称为 IPython notebook）是一个交互式笔记本，支持运行 40 多种编程语言。它的本质是一个 Web 应用程序，便于创建和共享文学化程序文档，支持实时代码，数学方程，可视化和 markdown。 用途包括：数据清理和转换，数值模拟，统计建模，[机器学习](https://edu.csdn.net/cloud/sd_summit?utm_source=glcblog&spm=1001.2101.3001.7020)等等 ，非常适合我们这里的数据分析
>
> jupyter 除了在专门的Jupyter Notebook中使用，也可以在pycharm和vscode中使用

```
pip install jupyter
```

将新的 Conda 环境添加到 Jupyter 核心中，可以通过以下步骤实现：

1. 激活环境

```bash
conda activate bioinformatics
```

2. **安装 `ipykernel` 包**

在激活的 Conda 环境中，安装 `ipykernel` 包，这样 Jupyter 才能识别并使用该环境。

```bash
pip install ipykernel
```

3. **将环境添加到 Jupyter 核心**

使用 `ipykernel` 命令将当前环境添加为 Jupyter 核心。你可以指定一个自定义的内核名称（比如 `myenv_kernel`），或者使用环境名称：

```bash
python -m ipykernel install --user --name bioinformatics --display-name "bioinformatics"
```

- `--name xxx` 是内核的名称（通常与 Conda 环境名称一致）。
- `--display-name "xxx"` 是显示在 Jupyter 中的内核名称，用户可以选择该名称来启动内核。

4. 使用pycharm/vscode 需要这里点击添加一下这个环境

![](https://pic.imgdb.cn/item/674d71bbd0e0a243d4dbe4fb.png)

## 练习

跑代码

- 直接用python脚本跑
  - ![](https://pic.imgdb.cn/item/674d762dd0e0a243d4dbe6fe.png)
- 用jupyter跑
  - [https://github.com/zmzhouXJTU/Python-Data-Analysis/tree/master](https://github.com/zmzhouXJTU/Python-Data-Analysis/tree/master)
  - ![](https://pic.imgdb.cn/item/674d71f4d0e0a243d4dbe51e.png)



# GSEA

## 理论部分

GSEA需要表达量的数据，GO/KEGG不需要

Ten years of pathway analysis: current approaches and outstanding challenges





## 实战部分

- 安装gseapy包

> [GSEApy-github](https://github.com/zqfang/GSEApy)
>
> [GSEAPY官方文档](https://gseapy.readthedocs.io/en/latest/introduction.html)

```python
# 使用 conda 安装（仅限 MacOS_x86-64 和 Linux）
conda install -c bioconda gseapy
 
# 使用 pip 安装
pip install gseapy
```



## 数据集结构

差异表达基因

里面有10813个基因

![](https://pic.imgdb.cn/item/6754439dd0e0a243d4dfc719.png)



| 列名               | 说明                                                         |
| ------------------ | ------------------------------------------------------------ |
| **Unnamed: 0**     | **基因的 Ensembl ID**（例如 ENSG00000160072）。通常用于唯一标识基因。 |
| **baseMean**       | 所有样本中该基因的**平均表达量**。基于原始计数（如 RNA-Seq 数据）计算得出。 |
| **log2FoldChange** | 两个条件之间的基因表达变化的对数2倍数。正值表示上调，负值表示下调。 |
| **lfcSE**          | log2FoldChange 的标准误差，反映了测量的不确定性。            |
| **stat**           | 差异表达统计量（如 Wald 统计量）。                           |
| **pvalue**         | **原始 p 值**，表示观察到的基因表达变化在零假设下出现的概率。 |
| **padj**           | **调整后的 p 值**（通常使用 Benjamini-Hochberg 方法），用于控制多重比较问题后的**错误发现率（false discovery rate,FDR）**。 |
| **Gene**           | 基因名称（如 ATAD3B）。                                      |



## 排序

新给大家的txt那个文件的数据集的Z值就是跟这个一样的**算好的**，用来排序，所以以下的内容当做原理参考一下就行

```python
df['Rank'] = -np.log10(df.padj)*df.log2FoldChange

df = df.sort_values('Rank', ascending = False).reset_index(drop = True)

df
```

- -np.log10(df.padj)：
  - np.log10(df.padj)：取调整p 值的以10为底的对数。
    - 由于 p 值通常是小数，取对数后数值变为负数，且越小的 p 值（越显著）对应的对数绝对值越大。
  - -np.log10(df.padj)：通过取负号，将对数后的 p 值转换为正值。这样，**较小的 p 值（更显著）对应的数值更大。**

- df.log2FoldChange：这是**基因表达变化**的对数2倍数。正值表示基因上调，负值表示基因下调。
- 二者相乘的结果，综合考虑基因的统计显著性和表达变化方向及幅度。因此当作Rank排序
- df.sort_values('Rank', ascending = False).reset_index(drop = True)
  - sort_values是排序函数，把表格按照'Rank'列
  - ascending = False表示降序排列
  - reset_index(drop = True) 因为排序后每一行都变了，所以索引要重新设置，并且丢弃掉原来的索引index
- 查看gene和rank两列

![](https://pic.imgdb.cn/item/675446a5d0e0a243d4dfc7a7.png)

至此完成了基本的预处理，也就是得到了后续分析的输入

## GSEA分析

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

```python
pre_res = gp.prerank(rnk = ranking, gene_sets = 'GO_Biological_Process_2021', seed = 6, permutation_num = 100)
```





- 先简单查看一下结果

```python
# 2. 打印 GSEA 结果的第一个键
print(list(pre_res.results.keys())[0])

# 3. 打印 GSEA 结果的第一个值
print(list(pre_res.results.values())[0])
```

结果展示一部分,这里的第一个并不代表是最富集的，因为还要看fdr和pvalue

```
regulation of cellular localization (GO:0060341)
{'name': 'prerank', 'es': -0.6650458489873552, 'nes': -1.0809540343472221, 'pval': 0.4166666666666667, 'fdr': 0.6882871982831866, 'fwerp': 1.0, 'tag %': '4/35', 'gene %': '6.83%', 'lead_genes': 'SPAG5;PARP1;KDM1A;HSP90AA1', 'matched_genes': 'LYN;WWC1;REEP6;PINK1;GSN;STXBP2;PARD6G;REEP5;LRP5;NR1D1;TRIM46;LRRK2;CAMK2D;BRSK1;DVL3;DYNC1H1;MAP2;KIAA1614;GOSR1;NUMA1;FER;CSNK1E;PPM1F;TTL;FES;CDK16;STXBP4;EFNA5;DVL1;EPHA5;HSP90AB1;HSP90AA1;KDM1A;PARP1;SPAG5', 'hits': [401, 530, 717, 1233, 1242, 1304, 1421, 1947, 1982, 1998, 2091, 2165, 2749, 2945, 3506, 3850, 4853, 5226, 5445, 5656, 6508, 6521, 6625, 7374, 7792, 7853, 8143, 8276, 8307, 8467, 9270, 10076, 10089, 10503, 10771], 'RES':
```

> - **Term**：基因集名称（如GO生物过程中的某个特定过程）
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
out = []

for term in list(pre_res.results):
    out.append([term,
               pre_res.results[term]['fdr'],
               pre_res.results[term]['es'],
               pre_res.results[term]['nes']])

out_df = pd.DataFrame(out, columns = ['Term','fdr', 'es', 'nes']).sort_values('fdr').reset_index(drop = True)
out_df
```

# GO富集



# K-mer

bionumpy



Rand, K.D., Grytten, I., Pavlović, M. et al. BioNumPy: array programming for biology. Nat Methods 21, 2198–2199 (2024). https://doi.org/10.1038/s41592-024-02483-4

















































