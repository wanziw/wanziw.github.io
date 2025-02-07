---
title: kaggle TF-binding 学习
date: 2025-02-01 22:05:07
categories: 深度学习
tags: 
  - 卷积神经网络
  - 样本不平衡
  - 生物信息
description: "kaggle上存的一些生物信息代码 尤其是TF-binding的学习"
---



> ["Bioinformatics" "community"](https://www.kaggle.com/discussions/general/203136)
>
> [Transcription Factor Binding Location Prediction](https://www.kaggle.com/code/shtrausslearning/transcription-factor-binding-location-prediction)

学习的主要是对样本不平衡数据的处理，对整一个染色体上的序列进行小段的切割，还有TF-binding问题的建模

其实最重要的数据处理部分还没有研究，如何把原始序列数据给处理成这里的.npy，有待日后进行学习

这个项目的意义是通过在一个染色体上训练一个模型来检测JunD转录因子的结合位点，从而推断出全基因组范围内的结合位点

# TF-binding

1. **生物过程的复杂性**：
   - 将核苷酸序列转化为氨基酸链（蛋白质）的过程看似简单，但实际上比我们想象的要复杂得多。
   - 虽然一个简单的模型可能会认为这种关系是直接的，但在现实中，有很多因素使得这一过程变得复杂，转录因子就是其中之一（它是调节DNA转录为RNA的蛋白质）。
   - 理解转录和翻译的复杂过程非常困难，尤其是对于那些没有深入了解这些过程的细节的人。
2. **深度学习的应用**：
   - 目标是使用深度学习预测转录因子将在DNA序列的哪些位置结合。这个问题可以被看作是一个二分类问题，模型需要识别一个转录因子是否会结合到某个特定的DNA位点。
   - 深度学习模型通过对大量DNA序列数据进行训练，寻找其中的模式，即使这些关系并不完全明确。
3. **笔记本工作流程**：
   - **生物概念介绍**：提供了DNA、RNA和蛋白质关系的背景知识。
   - **更现实的关系视角**：承认实际的生物关系更加复杂，并引入转录因子作为影响过程的关键因素。
   - **转录因子**：聚焦于建模转录因子的行为，它们在转录和翻译中起着至关重要的作用。
   - **实验数据**：数据（DNA序列）已经过预处理（可能采用了像独热编码（OHE）这样的技术），并被分成训练集、验证集和测试集。
   - 添加了如 `dnaseq_features` 这样的函数，以便在深度学习模型中一致地处理数据，确保不同数据集之间的预处理保持一致。

整体上，目的是通过机器学习技术理解一个复杂的生物过程，识别大型生物数据集中的模式。虽然这种方法非常强大，但它需要对生物学背景和如何有效应用机器学习技术有深入的了解。

# dataset

[Bioinformatics Collection](https://www.kaggle.com/datasets/shtrausslearning/bioinformatics/code)

- `.gb` 或 `.bk`
  - genbank格式的文件
  - 基因组注释
- .faa
  - fasta格式
  - 蛋白质序列
- .fnn
  - fasta格式
  - 核酸序列
- .seq
  - 原始序列数据
- 





# code

暂时还不知道前面是怎么进行预处理成为npy文件的

## 读取预处理后的数据code

读入数据

- 数据已经提前处理好成了npy格式的数据

> 数据与转录因子 **JunD** 相关，JunD 是转录因子激活蛋白 (AP)-1 家族的成员之一。这个实验的目的是识别 **JunD** 在人类基因组中的所有结合位点，并基于实验数据将这些信息存储在目标变量中。
>
> 实验数据中的基因组序列只包括 **22号染色体**，因为它的大小相对较小，只有大约 5000 万个碱基对。实验将基因组序列分割为每段 101 个碱基/字符，目标是找到每段序列中是否包含 **JunD** 结合位点的信息。每个序列片段的标签表示是否包含 **JunD** 结合位点（标签 0 或 1）。



```python
print(f"Training - Feature Matrix: {data.train['X'].shape}")
print(f"Training - Target Vector: {data.train['y'].shape}")
print(f"Training - Sample Weighting: {data.train['w'].shape}\n")

print(f"Validation - Feature Matrix: {data.valid['X'].shape}")
print(f"Validation - Target Vector: {data.valid['y'].shape}")
print(f"Validation - Sample Weighting: {data.valid['w'].shape}\n")

print(f"Test - Feature Matrix: {data.test['X'].shape}")
print(f"Test - Target Vector: {data.test['y'].shape}")
print(f"Test - Sample Weighting: {data.test['w'].shape}")
```

- 数据大小

```
Training - Feature Matrix: (276216, 101, 4)
Training - Target Vector: (276216, 1)
Training - Sample Weighting: (276216, 1)

Validation - Feature Matrix: (34527, 101, 4)
Validation - Target Vector: (34527, 1)
Validation - Sample Weighting: (34527, 1)

Test - Feature Matrix: (34528, 101, 4)
Test - Target Vector: (34528, 1)
Test - Sample Weighting: (34528, 1)
```

- 大概就是实验

- x是染色体序列，然后每段长度为101,并且one hot编码

- y是0或1，表示是否包含JunD结合位点

- w是权重，样本加权的作用是调整不同样本在训练过程中对模型的影响

  - 对于不平衡的数据集，样本加权可以帮助模型更好地学习少数类样本（例如 **JunD** 结合位点的出现频率可能较低）。

    样本加权可以通过 Keras 的 `class_weight` 或 `sample_weight` 参数进行传递，用于在训练过程中加大样本的权重，避免模型偏向某一类

- 此外还传入了一个ID值，用来对应每一条序列的x、y和w

## 切割序列code

对输入的 DNA 序列进行切割，并为每个片段生成 One-Hot Encoding (OHE) 特征，以便用于机器学习模型。

```python
def dnaseq_features(seq, start=0, n_segs=101, seq_name=None):
```



## Target Imbalance

目标不平衡，在训练集中有很少的样本是正类（即转录因子绑定到 DNA 序列的位点）

```python
# Target Value Counts
targ_weight = pd.DataFrame(np.concatenate([data.train['y'],data.train['w']],axis=1),columns=['y','w'])
targ_weight['y'].value_counts()
```

```
0.0    275048
1.0      1168
Name: y, dtype: int64
```

27万条是0，只有1168条是1，代表有结合位点

- 可视化目标变量和样本权重的关系
  - 可以查看每个样本在训练中的权重分配是否合理
  - 少数类样本（如 1 类）的权重被设定为更大的值，意味着模型训练过程中将更多关注少数类样本。通过绘制样本权重（`w`）与目标变量（`y`）的关系图
- `targ_weight.groupby('y').sum()`
  - 通过计算每个目标类别（如 0 和 1）在训练集中的权重总和，每一类的权重全部加起来
  - 我们可以检查权重是否分配得当。对于不平衡的类别数据集，少数类样本的权重总和应大于多数类。



## Model training

训练binary classifier

- 因为目标分布不平衡，所以我们要做**样本平衡**的处理
- 避免**过拟合**

为了考虑这两点，于是设置了三个模型，来考察

- model1
  - 去除dropout的，看是否过拟合的影响
- model2
  - 去除样本加权，看是否做样本加权平衡的影响
- model3
  - 采取了dropout和加权平衡的满血模型的效果



- 模型架构
  - 使用了三层的conv1d
- EVALUATION METRIC
  - ROC
  - AUC
- LOSS
  - **binary_crossentropy**
- 优化器
  - sgd

- 模型表现

  - 比较三个模型，AUC的结果说明
  - model1:正如预期的那样;模型开始显示出训练和验证结果之间的显著差异，评估仅达到了0.504的验证AUC，这可能表明在神经网络模型中添加dropout层是合理的。
  - 说明需要dropout
  - <img src="https://pic1.imgdb.cn/item/67a0ecddd0e0a243d4fa0d47.png" style="zoom:33%;" />
  - Model2:
    - 当我们没有对每个样本进行加权时，我们在训练和验证结果之间有非常小的差异，这就是我们想要的，说明dropout有用
    - 然而模型学习非常缓慢，只达到了0.58的验证AUC，这可能是表明样本不平衡是一个重要的问题，加权它们是合理的，需要加权<img src="https://pic1.imgdb.cn/item/67a0ecbcd0e0a243d4fa0cb9.png" style="zoom:33%;" />

  - model3
  - 效果都比较好<img src="https://pic1.imgdb.cn/item/67a0ed32d0e0a243d4fa0eb6.png" style="zoom:33%;" />









