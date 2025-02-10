---
title: jbrowse使用
date: 2025-02-10 23:34:49
categories: 生物信息工具使用
tags: jbrowse
description: jbrowse2使用记录
---

```text

# 首先创建文件夹，这里我暂时使用文件夹名为 “mydata” 代替
 sudo mkdir mydata //当前mydata是文件夹名称。
 # 创建 jbrowse 配置的第一步是加载基因组程序集：如果当前的服务器上没有samtools工具，请在服务器通过该命令下载该工具：
 sudo apt install samtools
 # 接下来需要通过我们自己的 FASTA文件生成一个“config.json”文件
 //假设当前fa文件名为 genome.fa
 samtools faidx genome.fa 
 //--out 后面的路径为需要生成config.json文件路径，当前暂时表示为刚才创建的文件夹路径
 // 注意！当前的genome.fa文件在 --load copy之后会复制一份到当前指定的文件路径下
 jbrowse add-assembly genome.fa --load copy --out /usr/local/jbrowse/mydata/
 # 生成config.json文件成功之后可以看到我们的config.json文件，此时可以重新启动 jbrowse项目查看我们刚刚生成的配置，通过路径地址加上 config.json文件指定路径获取。
 
 # 添加基因组信息，注意 track配置只能配置一个assembly，如果配置了多个assembly需要指定当前的 assemblyName，那么需要在当前的添加track的代码中加上
 --assemblyNames hg19
  //VCF格式
 bgzip file.vcf
 tabix file.vcf.gz
 jbrowse add-track file.vcf.gz --load copy --out /usr/local/jbrowse/mydata/
 
 //BED格式
 bgzip file.bed
 tabix file.bed.gz
 jbrowse add-track file.bed.gz --out /usr/local/jbrowse/mydata/ --load copy
 
 # 更多格式请参考官方文档：https://jbrowse.org/jb2/docs/quickstart_web/
 # 添加成功后重新启动jbrowse2项目，通过路径访问可以直接看到我们的项目
 http://ip地址:3000/?config=mydata/config.json
```

https://zhuanlan.zhihu.com/p/664086283

先是添加add-assembly 添加基因组 然后添加track annotation

这里

jbrowse sort-gff GCF_001879085.1_NIATTr2_genomic.gff | bgzip > GCF_001879085.1_NIATTr2_genomic.sorted.gff.gz
tabix GCF_001879085.1_NIATTr2_genomic.sorted.gff.gz
jbrowse add-track GCF_001879085.1_NIATTr2_genomic.sorted.gff.gz --load copy

这里不要copy，这里要inplace
