---
title: 生信Class5 MEGA分析
date: 2024-11-25 22:02:17
categories: 生物信息导论实验课
cover: /img/cover7.jpg
tags:
  - 多序列比对
  - 系统进化树
description: "生物信息学导论第五节课基本内容 mega软件使用 多序列比对 系统进化树"
---

生物信息学导论第五节课基本内容 mega软件使用 多序列比对 系统进化树

[常用生物学软件的安装与应用（四）—MEGA](https://zhuanlan.zhihu.com/p/337236253)

# 软件安装

[https://www.megasoftware.net/](https://www.megasoftware.net/)

MEGA的全称为Molecular Evolutionary Genetics Analysis，也就是专门用于**分子进化遗传分析**的一款软件。

软件是完全免费的，目前已更新到MEGA11，在官网就能直接下载安装。

下载时注意选择软件版本，包括Window/Mac/Linux三种，并根据电脑选择32/64位版本下载安装。网站也提供了详细的说明文档，在右上角菜单→【tutorial】→【walk through】目录下，有关于MEGA的详细操作说明。

![](https://pic.imgdb.cn/item/67456222d0e0a243d4d10c9f.png)

# 下载 序列数据

- NCBI中进行序列数据的下载，包括**基因/蛋白质**的
  - 链接：[NCBI](https://www.ncbi.nlm.nih.gov/)

> 我们这里作为例子，使用syp蛋白和其同源序列进行练习
>
> SYP（Synaptophysin，突触素）是一种重要的膜糖蛋白，主要存在于神经元的突触小泡中。



- 下载数据
  - 勾个十几个就行

![](https://pic.imgdb.cn/item/6745651dd0e0a243d4d110f5.png)

> 补充知识，关于fasta\fastq格式
>
> [全基因组测序（WGS）数据分析：第2节 FASTA和FASTQ](https://www.jianshu.com/p/624d9536d185)
>
> [[数据格式]（1）FASTQ和FASTA，SAM与BAM](https://zhuanlan.zhihu.com/p/48826465)

- 下载完成之后在MEGA中打开一下，当然自己也可以选择记事本看

![](https://pic.imgdb.cn/item/674565a2d0e0a243d4d111cf.png)

- 会问是否进行比对
  - 点击align



## 多序列比对

> **多序列比对(Multiple Sequence Alignment)**：多序列比对是一种基于序列比对的方法，它用于确定一组蛋白质序列或者核酸序列之间的相似性。通过比对多个序列，我们可以找出共享的进化保守区域，即那些在进化过程中保持不变的区域。这些保守区域通常对于蛋白质的功能和结构至关重要。

![](https://pic.imgdb.cn/item/67456667d0e0a243d4d1138a.png)

发现序列的长短不一，说明这只是初步的比对，还没有进行多序列对比的调整

![](https://pic.imgdb.cn/item/67456d06d0e0a243d4d12296.png)

- 提供了两种比对方式 ClustalW和MUSCLE
  - 需要填写一些参数，一般默认就行
  - 我们选择ClustalW进行比对
  - 可以看到进行了gap的填补，序列比对成功

> 关于原理：
>
> 序列比对(两条)：
>
> - [「一文搞定序列比对算法」Global以及Local Alignment序列比对算法的实现](https://zhuanlan.zhihu.com/p/571468890)
> - [b站序列比对动态规划矩阵生物信息学](https://www.bilibili.com/video/BV1cU4y1T7CG/)
>
> 多序列比对:
>
> - [多序列比对MSA](https://www.jianshu.com/p/a7a96ff355a7)
>
> 这些资料并不是最好理解的，可以自己去看更多的视频

![](https://pic.imgdb.cn/item/67456ea5d0e0a243d4d12313.png)

- 输出序列比对结果
  - Data->export->选择MEGA格式



![](https://pic.imgdb.cn/item/674573a9d0e0a243d4d124ef.png)



# 构建分子进化树

导入刚才生成的多序列比对结果: data里面选择



- C 保守的区域标黄
- V 不保守的区域标黄



![](https://pic.imgdb.cn/item/67457634d0e0a243d4d125a8.png)



- 建树

![](https://pic.imgdb.cn/item/67457679d0e0a243d4d125f5.png)



















