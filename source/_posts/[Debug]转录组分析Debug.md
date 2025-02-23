---
title: 转录组分析
date: 2025-02-23 19:53:31
categories: bug解决日记
description: "转录组分析过程中出现的一些bug"
cover: /img/cover31.jpg
tags: 生信分析
---



debug的部分可以单独记录成笔记

- 对于sra-tools这样下载linux软件系统不让的输入这个

```bash
sudo security list-keychains
```

- 单独debug htseq_count [error running htseq-count](https://github.com/htseq/htseq/issues/13)

```bash
htseq-count -q -f bam -i gene_id ./results/align/SRR6517663.bam ./data/genome/GCF_000317415.1_Csi_valencia_1.0_genomic.gtf > ./results/abundance/SRR6517663.count
```

- [samtools不能用的小问题](https://blog.csdn.net/qq_54478153/article/details/121855758)




