---
title: 《Spatial transcriptomic clocks reveal cell proximity effects in brain ageing》论文阅读
date: 2024-12-21 15:44:04
categories: 论文阅读
cover: /img/cover8.jpg
tags: 
  - 空间转录组学
description: "Nature"
---

[Spatial transcriptomic clocks reveal cell proximity effects in brain ageing](https://www.nature.com/articles/s41586-024-08334-8)、


> 这个工作比较简洁，记录下
	
【一句话】
	
整合1K植物RNA序列，注释，结构的Encoder预训练模型。
	
【数据】
	
来自1K植物转录组计划-图2；发表于2019年，1124个物种，一些活跃组织的转录组数据。 但是我没找到这个基模PlantRNA-FM是否在数据上做了一些平衡采样（似乎没），只选择了有对应蛋白注释的序列，2500万条序列，50B Token; 平均一条序列200长。
	
另外关于序列的标注-图3，用了5′ UTR, CDS and 3′ UTR regions注释信息，以及基于ViennaRNA的结构注释
	
【模型】
	
Encoder Only； 单核苷酸Token; 参数量35M；Dimension 480；12层Transformer。
	
预训练就是对应上面的三个目标：Mask任务，预测序列区域，和预测结构标注。但是没说权重占比。
	
预训练阶段的序列长度为512， 下游任务finetune长度到1024。
	
【下游任务】
	
找了两个新物种，去预测RNA的位置信息和结构。-图4
	
这个评测的确”作弊“，又是植物的RNA，又是和预训练一致的任务-尽管用了其他的物种，但是也在射程范围内。
	
----------------------------------
	
整体我觉得这个是证明了这事儿work, 不过1K个植物也不够，这个场景也的确很niche了，我都觉得可能非预训练模型也能达到类似的效果了。