---
title: '[深度学习]scFoundation代码实战'
date: 2026-09-07 19:39:52
categories: 深度学习
tags: 单细胞基础模型
cover: /img/cover18.jpg
---




# scFoundation


## 1. 数据处理 /preprocessing

### 1.1 论文部分

1. 收集数据集，来不同的数据库
2. 去重，每一个数据有一个对应的论文，doi号，手动收集，然后根据重复id删除
3. 统一raw count
   1. raw count直接用
   2. 如果提供的是 normalized 表达，就反推回 count：把矩阵里最小的非零值当成 1，其余非零值除以这个最小值再取整数部分
   3. 如果是 TPM / FPKM 这种无法反推的，就原样保留
4. 统一gene symbol，缺失的gene填0
5. QC：用 Seurat 和 Scanpy，只保留 表达基因数 > 200 的细胞（目的是过滤空液滴、极低质量、损伤细胞）

### 1.2 代码部分

> /preprocessing

- down.sh，用来下载数据，

  - 每个项目一个log目录，记录下载成功还是失败，以及别的信息
  - 每个项目在数据里也是单独的一个文件夹

- demo.sh，调用down.sh

  - **示例 1（10x Genomics 格式）**：先运行 `bash demo.sh` 下载 GEO 上的 10x 原始数据  （`barcodes.tsv.gz` / `features.tsv.gz` / `matrix.mtx.gz`），再用 `scanpy.read_10x_mtx()` 读取，  随后依次做 **基因符号统一 → QC → 保存 h5ad**。- 
  - **示例 2（CSV 格式）**：下载单个 gzip 压缩的 CSV（基因×细胞矩阵），用 `pandas.read_csv()` 读取，  流程与示例 1 相同。
  - 实际上![pasted_1787909885004_xiskok.png](https://pic1.imgdb.cn/i/034EuotW7pxXjOlLIx3Xs2.png)
  - [5min让你理解单细胞测序数据为啥有这么多格式](https://blog.csdn.net/weixin_47647983/article/details/156606115)
  - 这里没有做「normalized→raw count 反推」，代码里没写

- 下载的数据清单在Supplementary Data 1 & 2，分别整理了

- 「sample 级 + 每个样本细胞数」

- | project_ID | sample_ID | cell_number_reserved |
  | ---------- | --------- | -------------------- |
  |            |           |                      |

- 「project/研究级 + PubMed」

- | Project ID              | Study Title                                 | pubmed ID |
  | ----------------------- | ------------------------------------------- | --------- |
  | HCA-dcp6600438190759903 | A human cell atlas of fetal gene expression | 33184181  |

- demo.ipynb：穿插讲解。调用demo.sh以及scRNA_workflow.py 里面的函数

  - 对于不同格式数据读取，有时候要转置成行为细胞、列为基因
  - 基因符号统一，补0，重排
  - QC
  - 保存h5ad，这样子每个样本的格式就可以统一了

- scRNA_workflow.py ，存放函数代码

  - BasicFilter：过滤掉低质量的细胞和基因

  - QC_Metrics_info：计算并展示质控(QC)指标图，用于人工判断合适的过滤阈值

  - save_adata_h5ad

  - read_adata_h5ad

  - main_gene_selection(X_df, gene_list)，对每一个样本进行处理

    - 基因符号统一：把输入的「细胞 x 基因」表达矩阵对齐到目标基因列表 gene_list
    - 填充目标基因列表里有，但是当前数据里没有的gene
    - 按照list重新排gene顺序
    - 额外返回 var['mask']，标记哪些列是补零出来的(1=补零, 0=真实)

    

    



为什么demo.sh里面有一些项目要下载三个文件，有一些项目就只下载一个csv，我咋知道呢，他这里面有好几百个项目

是只有这两种格式吗

下载的是projectid还是sampleid呢

## 2.下采样

现在就能看清下采样的真正作用了：

- 如果没有下采样，标签永远和输入是同一个深度（同一个原始细胞），模型只能学"同深度的填空"；
- 有了下采样，你才能造出这种训练样本：输入 = 浅版，标签 = 深版；
- 换句话说，下采样不是"多喂一份数据给模型看"，而是**"造一个更难的题目 + 一份对应的标准答案"**。
  输入和标签的深度差，才是"Read-Depth-Aware"的训练内容；没有下采样，这个深度差就不存在。

> scFoundation 故意不把测序深度"归一化掉"，而是把总 count 作为显式信号（S/T token）喂给模型，让模型自己学
>   会"在不同 read depth 下对齐表达"。论文里把这叫 read-depth-aware (RDA) 建模





## 3.模型结构 /model

![pasted_1788167350783_iruyai.png](https://pic1.imgdb.cn/i/034Gc7rOk77n2VJ6XRno59.png)



### 3.1 get_embedding.py 

桥梁文件。把「预处理好的表达矩阵」转换成模型需要的输入，喂给预训练模型，并输出 cell / gene 两类 embedding。

> "预处理后的数据"→"归一化 + S/T token + 保留非零基因(gather)"→"喂模型"→"取get_embedding.py    cell/gene embedding" 全串起来。

---

```
输入表达矩阵
[N cells, genes]
        │
        ▼
对齐到 scFoundation 的固定 19264 个基因
        │
        ▼
逐个 cell 处理
        │
        ├── 表达值 normalize + log1p
        │
        ├── 计算 total count
        │
        ├── 构造 T token
        │
        └── 构造 S token
        │
        ▼
[19264 expression values + T + S]
        │
        │  shape = [1, 19266]
        ▼
value > 0 ?
        │
        ▼
gatherData()
只留下非零位置
        │
        ▼
例如 [1, 2302]
        │
        ├──────────────────────┐
        ▼                      ▼
表达值 embedding            Gene ID embedding
token_emb()                 pos_emb()
        │                      │
        └───────── + ──────────┘
                   │
                   ▼
             Transformer
               Encoder
                   │
                   ▼
             [1, 2302, D]
                   │
          ┌────────┼───────────┐
          │        │           │
          ▼        ▼           ▼
        S token  T token   所有 gene tokens
                              │
                         max / mean
                              │
          └──────────────┬────┘
                         ▼
              Cell embedding
```



---



**19264 是固定 gene vocabulary。** 输入数据必须映射到完全一样的 gene space 和顺序。

**基因表达值和基因身份是两种信息。**
 `token_emb(expression)` 告诉模型“表达多少”，`pos_emb(gene_id)` 告诉模型“这是谁”。

**T/S 是两个特殊 token。**
 `S` 表示当前 read depth，`T` 表示目标 read-depth/resolution，因此模型不仅知道表达 pattern，还知道测序深度条件。

**encoder 不跑 19264 个基因。**
 `gatherData()` 删除 0-expression genes，把 19266 压成大约几千个 token，从而显著降低 Transformer 计算量。

**cell 和 gene embedding 来自模型不同位置。**
 cell embedding = encoder 上的 `S + T + max genes + mean genes`；gene embedding = decoder 中完整 19264 gene space 的 hidden representation。





### 3.1.1 Q1

- 为什么preprocess已经做过的main_gene_selection这个补0，这个getembedding里面还要再做一遍
- 因为 preprocessing/ 和 get_embedding.py 是两个独立入口，服务的是两类完全不同的用户。前者是作者自己，后者是其他用户（拿自己的数据做推理）， 用户随便给的 csv/npy/h5ad。普适性很好
- 里面有一个检测，如果是对齐好的，就不会重复进行

```python
 if gexpr_feature.shape[1] < 19264:        # 只有基因数不够时才补
      gexpr_feature, to_fill_columns, var = main_gene_selection(gexpr_feature, gene_list)
      assert gexpr_feature.shape[1] >= 19264

```





### 3.1.2 面对不同场景的设计

考虑的太全面了，要从项目最开始设计之初就学习



>   第 1 层：读入       (文件格式：4 选 1)
>   第 2 层：基因统一   (自守卫：不够才补)
>   第 3 层：归一化     (input_type × pre_normalized)
>   第 4 层：拼 T/S     (input_type × tgthighres)
>   第 5 层：gather     (统一，无分支)
>   第 6 层：取输出     (output_type × pool_type)
>
>   每一层只关心自己那一件事，处理完交给下一层。所以读代码时按层读，不要试图在脑子里展开所有组合——那样当然会晕。



```
你可以直接抄走的 6 条设计原则

  1. 边界防御：所有外部不确定性（格式、基因数、是否归一化）在入口一次性收敛，内部只面对规范化数据。
  2. 把"不确定"显式化：不确定的事（是否已归一化）不要猜，设个参数让调用者声明（--pre_normalized）。
  3. 字符串前缀做轻量策略：t/f/a 一个参数编码多种策略，比参数爆炸优雅（--tgthighres）。
  4. 一个入口 + 枚举开关：多任务用 output_type 分派，而不是复制多个脚本。
  5. 幂等自守卫：if shape[1] < 19264 让"已对齐"和"未对齐"的输入都安全。
  6. fail-fast：每个分支末尾 raise ValueError('...must be ...')，非法输入立刻报错，不静默跑错。

  ———

  等你写 PlantFormer 的推理入口时，可以对着这个清单问自己：我的输入可能有哪些格式？可能有没有归一化？可能有哪几种输出
  粒度？ 把答案变成参数和分支，你的代码自然就"规范"了。
```



1. 数据不同输入格式
   1. npz / h5ad / npy / csv

2. bulk的还是singlecell的
   1. 模型是sc训练的，但是只要gene可以对齐，也可以使用bulk的数据。相当于输出的是sample embedding而不是cell embedding

2. 组装token T和S。根据pre_normalized：T/A/F，用户给我的数据做过归一化吗
   1. T，已归一化+log1p，直接用
   2. F，raw count，程序做normalize+log1p
   3. A，已归一化，原始测序深度也附在最后，专门给 GEARS 扰动预测任务
   4. 默认是F，raw count
3. tgthighres：t / f / a
   1. f、a、t
   2. 对应三种下游需求：想「读深翻倍」就说 f2，想「绝对深度」就说 t4，想「加一点」就说 a5。
4.  不同粒度的输出output_type：cell / gene / gene_batch / gene_expression
   1. 细胞级表示
   2. gene级表示
   3. 一批细胞表示， GEARS（单细胞基因 embedding 太大，要 batch）
   4.   gene_expression    重建的表达值    
5.  pool_type：all / max
   1.  cell 输出的聚合策略：all=4 路拼接（T/S + max + mean），max=整体 max。
   2. 这个max是每个维度取某个gene在这个维度的最大值，相当于每个维度对应不同gene
6.  version：ce / rde / noversion
   1. 模型选型：ce=通用 embedding，rde=读深增强，noversion=用户自定义 checkpoint 路径。对应 checkpoint 里存的多个子模型。
7.  --demo
   1.   调试的快速通道：先用 10 个细胞验证流程通不通，再跑全量。这是工程里非常实用的习惯。



我觉得他这个代码写的非常的规范，面对不同的使用场景，我想学一下他这个设计的规范，是考虑了哪些主要的场景。我感觉有很多排列组合和分支，我都搞不太明白，我作为一个小白，我在刚开始写代码的时候肯定不会注意到这些场景的，但是这个代码确实考虑到了很多很多，写的很规范，所以帮我好好拆解一下



S、T更像一个初始值会变的【CLS】

## 3.2 load.py

工具箱函数

 数据侧工具：gatherData（把稀疏表达压成短序列）、main_gene_selection、            load_model_frommmf（checkpoint 读取 + config 转换）





## 3.3  pretrainmodels/mae_autobin.py

 模型本体：AutoDiscretizationEmbedding2（连续表达值自动分箱成 embedding）和
           pretrainmodels/     MaeAutobin（encoder→decoder 的完整前向）







## 3.4 pretrainmodels/transformer.py+performer.py

编码器到底用的什么：标准 Transformer block 和 Performer（线性注意力）



## 3.5 finetune_model.py

怎么冻结骨干、只微调最后几层、接分类头（你以后植物下游任务要照抄的模板）



## 3.6 training_hyperparameter.txt

回看预训练配置（768 维、12 层、12 头、mask 概率等），把代码和论文参数对上      

  













