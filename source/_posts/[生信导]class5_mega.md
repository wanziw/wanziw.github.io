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

[toc]



# 概念介绍

## 多序列比对

多序列比对（multiple alignment），对两条以上的生物序列进行全局比对

![](https://picx.zhimg.com/v2-ccbc7d76d3c6d0f835de7d4e78508b0d_1440w.jpg)

- 注意事项

一般10-15条序列，两两间序列相似度30%-90%，序列差不多长，没有重复域

![](https://picx.zhimg.com/v2-d75f290e82b639a1307e1bd342d54965_1440w.jpg)

## 系统进化树

系统进化树是对多序列比对（MSA）结果以树形图形式的一个呈现，对于研究进化关系有很大的帮助，通过进化树分析我们也可以关键功能基因和蛋白得出一些假说

![](https://i-blog.csdnimg.cn/blog_migrate/4609a84cb75d0d68a1f9a81ad1d2d66c.jpeg)

上图很好的反映了进化树构建的依据：

1. 随着物种进化的演绎，进化水平越相近的物种他们的序列越接近
2. 如果是由同一个物种演化过来的，分化出来的不同物种会保留共同祖先的印记，这是区别于其他的祖先的。

![](https://upload-images.jianshu.io/upload_images/26457016-94154539a558da58.png?imageMogr2/auto-orient/strip|imageView2/2/w/555/format/webp)









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
  
- > ClustalW和MUSCLE，ClustalW首先对序列做两两比对，根据该两两比对计算两两[距离矩阵](https://zhida.zhihu.com/search?content_id=245454596&content_type=Article&match_order=1&q=距离矩阵&zhida_source=entity)，是一种经典的比对方法，比对速度慢但精确度较高，使用范围也比较广泛。Muscle的功能仅限于多序列比对，速度快，序列数很多的话建议选Muscle，但精确度不如ClustalW。这里我们选ClustalW，参数默认即可。

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
> 这些资料并不一定是最好理解的，可以自己去看更多的视频

- 这里可以先修剪 上面有个小剪刀标志 修剪两段多余的序列
  - 两端对齐 减少相似性低的部分，可以增加进化树构建成功的概率
  - 选择区域然后右键 delete也是一样的效果


![](https://pic.imgdb.cn/item/67456ea5d0e0a243d4d12313.png)

- 输出序列比对结果
  - Data->export->选择MEGA格式



![](https://pic.imgdb.cn/item/674573a9d0e0a243d4d124ef.png)

> 由于上课内容的时间限制，这里真正做的时候还需要大家对序列名字重新命名，不然乱乱的
> 可以参考这篇[**序列预处理**](https://zhuanlan.zhihu.com/p/342713574)

# 构建分子进化树

导入刚才生成的多序列比对结果: data里面选择



- C 保守的区域标黄
- V 不保守的区域标黄
  - 可以对不保守的区域进行手动删除
- 分组
  - 可以1


![](https://pic.imgdb.cn/item/67457634d0e0a243d4d125a8.png)



- 建树
  - 最大似然法
  - 邻接法
  
- > 这里有三种方法，分别是最大似然法 (Maximum Likelihood)、邻接法 (Neighbor-Joining) 和最小进化法 (Minimum Evolution)。【这三种方法我就不在这里介绍了，大家可以去查查，常用**邻近法**】
  >
  > 补充：
  > 一般情况下，若有合适的分子进化模型可供选择，用最大似然法构树获得的结果较好；对于近缘物种序列，通常情况下使用最大简约法；而对于远缘物种序列，一般使用邻接法或最大似然法。对于相似度很低的序列，邻接法往往出现长枝吸引(branch attraction)现象，有时严重干扰进化树的构建。对于各种方法重建进化树的准确性，Hall (2005)认为贝叶斯法最好，其次是最大似然法，然后是最大简约法。其实如果序列的相似性较高，各种方法都会得到不错的结果，模型间的差别也不大。邻接法和最大似然法是需要选择模型的。蛋白质序列和DNA序列的模型选择是不同的。蛋白质序列的构树模型一般选择Poissoncorrection(泊松修正)，而核酸序列的构树模型一般选择Kimura2-parameter (Kimura一2参数)。如果对各种模型的理解并不深入，最好不要使用其他复杂的模型。参数的设置推荐使用缺省的参数。


![](https://pic.imgdb.cn/item/67457679d0e0a243d4d125f5.png)

- 参数选择

> 参数意义
>
> 检验方法一般采用Bootstrap 进行检验。也叫自举法检验，用来验证每个分支的可靠性，后面可以展示在分支处，次数至少1000次。

![](https://pic.imgdb.cn/item/6749af34d0e0a243d4db41c9.png)



# 简单调整树

- 三种树的形状
  - 上面一排有两个树形的按钮，可用于改变进化树的形状，包括矩形、辐射形和圆圈形（下图从左到右），也可以调整序列名称是否对齐

- 树的风格调整
  - 一般数量大我们会选择调成圆形

- 导出
  - Image 导出各种样子的
  - 如果后续还需要没话，在FILE中寻找newick模式
    - <img src="https://pic.imgdb.cn/item/674c7194d0e0a243d4dba736.png" style="zoom:25%;" />

# iTOL绘制系统发育树

> 获得nwk格式的进化树后，需要对其进行展示，以便从直观上判断材料间的聚类关系，界面版的MEGA自带简单的展示功能，可以对进化树进行展示，但其功能较为简单，无法满足着色、添加额外信息等较为个性化的要求。从功能的丰富度来说，iTOL(https://itol.embl.de/)、EvolView(http://www.evolgenius.info/evolview/)、ggtree(https://github.com/GuangchuangYu/ggtree)应当是功能较为齐全的软件，其中，ggtree是R软件包，可以在本地操作，但需要编写代码，使用起来并不十分方便。三款软件中，从操作的简易度，效果的美观程度来看，iTOL都是最佳的选择，下面将以iTOL为例子，说明对进化树结果的展示方法。

我们导出newick模式的树文件，在iTOL中上传

- 网站：[itol](http://itol.embl.de/)

![](https://pic.imgdb.cn/item/674c7090d0e0a243d4dba706.png)

- 上传之后点击文件就可以进入编辑界面
  - 左侧是进化树文件，右侧是工具栏。ITOL中提供了各种美化进化树的方法，工具栏中可以调整字体、颜色、分支长度等参数，用鼠标右键点击序列名称也可以调整字体。
  - 鼠标滚轮可以放大缩小，左键按住可以拖动。
  - ![](https://pic.imgdb.cn/item/674c729ed0e0a243d4dba766.png)
- 树的形状“Mode”
  - 网站默认的竖直的树为”Rectangular”，也就是矩形树，可以点击旁边的“Circular”变成圆形或“Unrooted”变成无根树。“Invert tree”是翻转树，点击后会把每条支的Label放在里面，树结构放外面。
- 标签的格式“Label options”
  - 可以更改字体样式，下面“Alignment”是设置字体往哪里对齐；“Branch options”是设置支的形状，“Line style”可以设置粗细，后面的图案是改变支类型。下面的“Dashed lines”是设置支末端伸出虚线的样式。都设置完成后就完成了第一步

- 一些别的参数
  - 大家可以自己试试调整就会发现是调什么的
  - ![](https://pic.imgdb.cn/item/674c73bcd0e0a243d4dba7a4.png)
- 设置标签颜色
  - 下一步就需要设置标签颜色。我们在研究过程中，总会有几个关注的物种或分支，这时候为了进化树更加直观明了，就需要用把我们关注的支和标签突出显示
  - “Color Range”可以对这个支标注一个背景色块，点击之后，创建一个色块并命名，这样标注好了，旁边的“Clade”和“Full”可以选择背景色块的区域大小。
  - 另外，还可以通过“Branches”设置支颜色，“Labels”设置标签颜色，大家可以自己探索一下。

![](https://pic.imgdb.cn/item/674c7719d0e0a243d4dba813.png)

![](https://pic.imgdb.cn/item/674c7734d0e0a243d4dba819.png)

- 至此，关于系统进化树的构建和美化的基本内容已经讲完了，让大家有个基本的概念，在论文中看到了这样的图知道是干什么的和怎么做出来的。
- 未来大家如果需要在论文中作图的话，需要自己再多去了解一些美化，比如配色方案、物种的分类注释的内容

> 更多参考链接：
>
> [iTOL快速绘制颜值最高的进化树！](https://blog.csdn.net/qazplm12_3/article/details/143021316)
>
> [系统发育树的美化（iTOL）](https://blog.csdn.net/qq_45735120/article/details/131121748)
