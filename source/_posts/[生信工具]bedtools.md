
---
title: bedtools使用记录
date: 2024-09-9 13:44:50
categories: 生物信息工具使用
tags: bedtools
description: bedtools使用记录
Copyright: true
copyright_author: wanzi
copyright_author_href: https://github.com/wanziw
copyright_url: http://wanziw.club/2024/09/09/%5B生信工具%5Dbedtools
copyright_info: 此文章版權歸wanzi所有，如有轉載，請註明來自原作者
---



# bedtools

## BED format



![](https://pic.imgdb.cn/item/66de5dd1d9c307b7e950d2b5.png)



- BED的全称是“Browser Extensible Data”，用于存储基因组区域
- BED文件包含基因组区域的信息。
  - **0-based坐标系**：使用0作为基因组坐标的起始点。
- **Tab (\t)**分隔的，每一行代表一个基因组区域
- 命令行工具
  - BEDtools 命令行工具
  - [文档链接](https://bedtools.readthedocs.io/en/latest/)

![](https://pic.imgdb.cn/item/66de5fb6d9c307b7e952cb07.png)

- BED文件必须包含
  - `chrom`（染色体）: 表示基因或者基因组段所在的染色体。
  - `start`（起始点）: 表示基因组段起始位置的坐标。
  - `end`（终止点）: 表示基因组段终止位置的坐标。
- 两种数据格式
  - UCSC BED：专门为使用UCSC基因组浏览器设计的格式
  - Everything else：不同的软件或数据库。

![](https://pic.imgdb.cn/item/66de714dd9c307b7e96ce7e1.png)

可以为每个基因的位置添加分数，然后来进行生物信息的操作

## 0-base vs 1-base

![](https://pic.imgdb.cn/item/66de72c6d9c307b7e96ec4e8.png)

- 不同类型的坐标系

![](https://pic.imgdb.cn/item/66de73d1d9c307b7e96ffece.png)



- 一个不太精确的经验规则，即如果文件的内容是以文本形式直观易读的，那么它可能使用的是1-based坐标系统。这种经验规则并不是绝对的，但是在处理文本格式的生物信息文件时，这可以作为一个初步的判断依据。



## Convert VCF to BED with awk

将VCF文件转换为BED文件

```bash
grep -v "#" 1000G_omni2.5.b37.sites.vcf | awk '{ print $1"\t"$2-1"\t"$2"\t"$3 }' > 1kgp_omni2.5.hg19.bed

```

> **grep命令**：使用`grep -v "#" 1000G_omni2.5.b37.sites.vcf`这个命令从VCF文件中过滤出所有非注释行（即不含“#”的行）。这些行通常包含关于变异位点（如单核苷酸多态性，SNPs）的具体数据。
>
> **awk命令**：通过管道`|`将grep的输出传递给awk命令处理。awk命令用于处理文本数据和生成格式化报告。这里的命令`awk '{ print $1"\t"$2-1"\t"$2"\t"$3 }'`执行以下操作：
>
> - `$1`：打印第一个字段，通常是染色体名。
> - `$2-1`和`$2`（**重点**）：因为VCF文件是1-based（即坐标从1开始），而BED文件是0-based（坐标从0开始），所以将起始位置减1，将结束位置设为原始起始位置，以转换坐标系统。
> - `$3`：通常为变异位点的ID。
>
> **输出重定向**：最后的输出通过重定向`>`保存到一个新的BED文件`1kgp_omni2.5.hg19.bed`中。

- 为什么使用BEDtools
  - 在基因组学分析中，经常需要研究特定的基因组区域对疾病或表型的影响。**使用BEDTools可以方便地将变异数据（VCF格式）与感兴趣的区域**（如特定基因、已知敏感或黑名单区域）进行相交分析，从而识别重要的基因组变异。



## sorted BED files

unix sort command

- 命名文件 分享的时候，在文件名后面最好打上参考基因组

这张图片显示了一系列在命令行中使用的命令，它们涉及到对BED文件的排序、压缩、检查大小和索引。这些命令是：

1. **排序 BED 文件**:
   ```bash
   sort -k1,1 -k2,2n 1kgp_omni2.5.hg19.bed > tmp; mv tmp 1kgp_omni2.5.hg19.bed
   ```
   这条命令将`1kgp_omni2.5.hg19.bed`文件按照染色体名（第一列）和起始位置（第二列）进行排序。结果首先写入临时文件`tmp`，然后用`mv`命令将`tmp`文件替换原文件。

2. **压缩 BED 文件**:
   ```bash
   bgzip -f 1kgp_omni2.5.hg19.bed
   ```
   使用`bgzip`命令压缩排序后的BED文件。`-f`选项强制压缩，即使目标文件已经存在也会被覆盖。

3. **查看压缩文件的大小**:
   ```bash
   du -sch 1kgp_omni2.5.hg19.bed.gz
   ```
   `du`命令用来检查文件大小。`-sch`选项表示：
   - `-s`：仅显示总计。
   - `-c`：除了列出各个文件的大小，还要显示所有文件的总和。
   - `-h`：以易读格式（如K, M）显示大小。
   这个命令显示压缩后的文件大小为26M。

4. **索引压缩文件**:
   ```bash
   tabix -p bed 1kgp_omni2.5.hg19.bed.gz
   ```
   `tabix`是用于索引基于文本的数据文件的工具，使得可以快速检索文件中的某个区域。`-p bed`指定了文件格式为BED，这是必要的参数，以便`tabix`知道如何解析文件。

