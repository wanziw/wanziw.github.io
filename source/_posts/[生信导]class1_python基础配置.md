---
title: 生信Class1 anaconda、pycharm安装和配置
date: 2024-11-04 17:21:37
categories: 生物信息导论实验课
tags: python教程
description: "生物信息学导论第一节课基本内容"

---





https://wanziw.club/

# 课程介绍

- 助教：
  - 王子轩
  - 谢璐瑶

- > 课程内容（不全版）
  >
  > 1. R和python基础
  > 2. 使用R语言中的DESeq2包做基因差异表达分析，ggplot2绘制火山图、热图
  > 3. 使用MEGA构建不同物种的系统发育树
  > 4. 使用pyMol可视化蛋白质结构，分析结构和功能的关系
  > 5. kmer法探究基因kmer分布，获得序列向量进行聚类和分类

- 本人的一些链接

  - [个人博客](https://wanziw.club)
  - [csdn](https://blog.csdn.net/weixin_57345774)
    - 对于编程比较感兴趣/记忆力不太好的同学推荐使用博客记录自己学习内容
      - csdn/简书/自己搭网站

  - [github](https://github.com/wanziw)

  

  

# 基础概念

- python
  - 编程语言
  - 解释器，用来发挥
- pycharm/vscode
  - 编辑器，开发工具，提供敲代码的界面
- python包
  - numpy pandas pytorch
  - 第三方包
- anaconda/conda 
  - 包管理工具，管理不同的项目和环境

# 环境的配置

对于不同的项目，我们一般在**命令行**使用**conda**配置不同项目的环境，这样python解释器的版本和第三方包的版本就是相互独立的

然后再使用开发工具开发

![](https://pic.imgdb.cn/item/67289739d29ded1a8ca92c45.png)

![](https://pic.imgdb.cn/item/6728978cd29ded1a8ca9a92d.png)

![](https://pic.imgdb.cn/item/672897dcd29ded1a8caa1adc.png)

# 安装anaconda

博客：[Anaconda安装（2024最新版）](https://blog.csdn.net/m0_66047447/article/details/141110995)

[anaconda官网](https://www.anaconda.com/)

[anaconda官网清华镜像](https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/)

- 安装步骤
  1. 一路next
  2. 安装路径最好是写d盘（默认c盘）
     1. d盘创建一个文件夹 D:/anaconda3    or   D:/software/Anaconda3 
        1. 按自己习惯
        2. 路径上最好不要有中文
     2. 这样好找且不浪费c盘空间
  3. 勾选上第二个默认安装一个python版本3.11/3.12![](https://pic.imgdb.cn/item/67289aa3d29ded1a8cae3736.png)

- 等待一段时间



# 配置anaconda环境

- 更改系统环境变量
  - 电脑搜索“环境变量”/“查看高级系统设置”  -> “环境变量”
  - Path->编辑->新建
  - 要根据自己的安装路径来

```
D:\Anaconda3
D:\Anaconda3\Scripts
D:\Anaconda3\Library\bin
D:\Anaconda3\Library\mingw-w64\bin
D:\Anaconda3\Library\usr\bin
```

![](https://pic.imgdb.cn/item/67289d1fd29ded1a8cb21072.png)

```
conda --version # 查看conda版本
python # 打开python环境
print("hello world")
```



- anaconda换源

```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
 
//设置搜索时显示通道地址
conda config --set show_channel_urls yes
 
```

- 修改默认虚拟环境安装位置，以后配置conda环境好找
  - "D:\software\anaconda\envs"这部分根据自己的来

```
conda config --add envs_dirs D:\software\anaconda\envs
```

- 可能出现的问题，出现文件权限的问题的时候
  - ![](https://pic.imgdb.cn/item/67289f49d29ded1a8cb45890.png)
  - 全部钩上允许
  - ![](https://pic.imgdb.cn/item/67289f9cd29ded1a8cb49ee4.png)









# conda常用命令

D:\software\anaconda\envs

​	1.查看当前conda版本

```python
conda -V
conda --version
```

conda对虚拟环境的管理

1. 查看已有的虚拟环境列表

```python
conda info --envs
conda info -e
conda env list
123
```

创建虚拟环境

```python
conda create -n test python=3.11

# -n也可以使用--name，python368是创建的新虚拟环境的名称
# python= 后面是指定虚拟环境中python的版本号
# 可以使用命令conda search python搜索有哪些可安装的python版本
# 可以加入-y，则创建过程中不用再输入y确认安装包
1234567
```

3.激活 / 切换虚拟环境

```python
conda activate test
```

4.退出虚拟环境

```python
conda deactivate
```

# 安装pycharm

[2024最新版PyCharm安装使用指南](https://blog.csdn.net/jackson_lingua/article/details/135860415)

[pycharm官网](https://www.jetbrains.com/)



安装社区版

下载在d盘上面



创建项目

配置python解释器



# 安装vscode

d盘创建一个vscode



# 课后总结

> 1. 编程这块大家有问题**多百度**，**报错**是很正常的，不用怕。
> 2. 今天上课的内容对0基础的大家来说其实难度很大了，能按流程做下来的同学已经很厉害了，这一套下来一般自己瞎鼓捣得一个礼拜，我自己也是编程了一年多后才能慢慢理清这些。
> 3. 学会了这块之后，后面进行python生信分析。对每一个项目，**创建好项目文件夹，创建好conda环境**，就可以用pycharm打开文件夹开始运行代码了
> 4. 因为课程时间限制，我们对python的基础就只有这一节课的时间讲。用vscode的同学、对python的数据分析和语法感兴趣的同学可以去**b站**找视频看。计算机不像生化环材，技术迭代块，学校里一般教的比较落后，我本科都是靠自学，网上开源的教程质量都很不错。
> 5. 写博客的语法是**markdown**，生物信息专业的同学推荐学习一下，学会了还可以用来水98
> 6. 我们先前打开的anaconda prompt和vscode里面打开的终端是一个东西，mac里叫命令行，windows叫cmd。
>    1. 在这里可以创建conda环境，安装新的包。
>    2. 安装新的包也可以在pycharm里点点添加，后续会讲
> 7. 对编程、机器学习、深度学习感兴趣的同学有问题可以私信找我或者➕v





接下来给大家列了大家问的问题，有相同的问题的同学可以照着解决一下

## 问题1 conda-envs-scripts里面没有conda.exe

课后有个同学也问了这个问题当时我没整出来

就是这个conda.exe不是在anaconda3\envs\scripts这个目录下而是在anaconda3\scripts这个目录下，那我们就选择这个anaconda3\scripts\conda.exe，然后选完后点**加载环境**，**使用现有环境**里面选择自己创建的的环境就好了


![](https://pic.imgdb.cn/item/6728e1a0d29ded1a8cf5c6ec.png)
![](https://pic.imgdb.cn/item/6728e1a1d29ded1a8cf5c822.png)

## 问题二 CondaError: Run 'conda init' before' conda activate

命令行里没能激活conda环境的

![](https://pic.imgdb.cn/item/6728e19ed29ded1a8cf5c5d5.png)

使用管理员身份打开cmd

![](https://pic.imgdb.cn/item/6728e1e4d29ded1a8cf5ff0c.png)
