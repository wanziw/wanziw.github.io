---
title: 生信Class6 numpy/pandas
date: 2024-12-02 16:57:33
categories: 生物信息导论实验课
cover: /img/cover16.jpg
tags:
  - python
  - 数据分析
sticky: 1
description: "生物信息学导论第六节课铺垫内容 numpy和pandas的基本使用"
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

















































