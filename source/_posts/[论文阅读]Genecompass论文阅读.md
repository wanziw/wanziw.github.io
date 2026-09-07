---
title: 《GeneCompass》论文精读
date: 2026-08-09 21:26:37
categories: 论文阅读
cover: /img/cover9.jpg
tags: 
  - 单细胞基础模型
description: "研究者将基因相关的先验知识融入模型，成功训练了 GeneCompass，一个能够、全面地理解复杂的基因调控网络的单细胞基座模型。"
---


# GeneCompass: deciphering universal gene regulatory mechanisms with a knowledge-informed cross-species foundation model



> 别的博客解读,搭配食用更佳：
>
> [(十一) GeneCompass | 知识驱动的跨物种单细胞基座模型](https://zhuanlan.zhihu.com/p/8553664471)
>
> 关注模型训练和算法：[文献--单细胞组学大模型之Geneformer](https://lishensuo.github.io/en/posts/basic/205-geneformer/)
>
> 论文每一段的解读:[人工智能 | Cell Research | GeneCompass：用知识驱动的跨物种基础模型解析普遍的基因调控机制](https://zhuanlan.zhihu.com/p/14717627468)



Genecompass 基于知识驱动的跨物种基础模型

优势就在于整个不同物种的数据集

- GeneCompass

> 预处理阶段保留了在各数据集中具有足够表达差异性或表达水平的基因，以捕捉生物异质性和细胞类型特异性特征。最终数据集包含 36,092 个基因，其中 17,465 个为人类和小鼠的[同源基因](https://zhida.zhihu.com/search?content_id=250733522&content_type=Article&match_order=2&q=同源基因&zhida_source=entity)，5,649 个为人类特有基因，12,978 个为小鼠特有基因。

- 输入层：

  - 取表达量最高的2048个gene
  - 每个gene token 包含
    - gene id
    - 绝对表达值
    - 表达量排序
    - 物种信息
      - 额外token
    - 四类先验知识
      - GRN
        - GRN里面的gene坐标然后使用gene2vec
      - 启动子序列
        - 一些bert模型转换来的embedding
      - 基因家族，同GRN
      - 共表达关系，同GRN
  - 12层Transformer

- ![](https://pic1.imgdb.cn/i/03447vEuGyV6qslo6a4fGM.png)

  



- fig2

![](https://pic1.imgdb.cn/i/03448FYf2R9T2nd6QxFpqW.png)

- fig2只要是训练完模型之后，判断内部学到的 gene embedding 到底有没有生物学意义。

- 2a判断的是物种间同源关系有没有学到

- 后面几个图的是判断基因调控关系。

选择了2000个人/小鼠的B cells

现在每个gene通过模型之后会生成一个embedding，计算embedding之间的余弦相似度就可以比较gene间的关系

1. 同源gene的相似度比非同源的高，说明模型学到了同源关系

   1. 为了防止被诟病，预训练的时候给了homology信息。于是做了几组补充比较

   2. > 1. 有pretraining + 有prior knowledge
      >
      > 2. 有pretraining + 没有prior knowledge
      >
      > 3. 没有pretraining + 有prior knowledge
      >
      > 4. 非同源基因作为baseline

   3. 发现prior knowledge 有贡献，
       但 self-supervised pretraining 的贡献更大。主要还是模型学习到了这个关系

2. fig2a右边的意思确认是同一个 species 里面，**不同 gene** 的 embedding 是否还能被区分？

   1. 作者发现不同 gene 并不是全部塌缩成一样的 embedding，因此认为模型仍然具有 gene distinguishability。

---

```
   左：
   
   该相似的 homolog
   确实比较相似
   
           +
   
   右：
   
   不该全部相同的不同genes
   也没有全部塌缩
   
           ↓
   
   embedding既有跨物种同源性
   又保留gene之间的区分性
```

---

4. fig2B

   1. 模拟删除gene，是模型训练完成之后，参数不动，把这个gene从输入中移除
   2. 重新跑模型得到每个gene的embedding
   3. 然后比较cosine
      1. GeneCompass 的 gene embedding 是 contextual 的，所以删除 GATA4 会改变其他 gene 所处的“上下文”
      2. 如果某些 gene 的 embedding 因此特别明显地变化，而且这些 gene 恰好就是实验已知的 GATA4 direct targets，那么说明模型内部确实编码了与真实调控关系一致的信息。

- 同一个gene在不同cell里面的数据是一个样本点，所以用的箱线图





- Fig3

预训练的时候它做的是：

---
```
MASK gene
↓
猜Gene ID
+
猜Expression
```
---


它并没有主要通过：

```
这个cell = B cell
```

---

这种人工标签训练。

所以预训练结束后，GeneCompass 更像一个：

> **已经学了很多细胞和基因规律，但还没专门学“细胞分类”这门课的学生。**

然后 Fig. 3 做 **fine-tuning**。

使用真实的细胞类型标签，在cell embedding后添加一个全连接层，用交叉熵作为损失函数预测细胞类型



```
预训练
大量无标签cell
↓
学“细胞世界的基础规律”
↓
GeneCompass


Fine-tuning
少量有cell-type标签的数据
↓
专门学习细胞分类
```
---



> 想做好一个human下游任务，并不一定只喂human数据最好。加入mouse数据，反而可以帮助。
>
> 跨物种预训练，可以反过来提升单物种任务。

后面就是在证明模型可以在不同的组织里面区分细胞类型。



- 离谱的fig3d
  - Mouse 作为 reference species，Human 作为 target species。使用CAME模型，把 CAME 原本的 gene representation 换成 GeneCompass 学到的 gene embedding，会不会更好？
  - came本身需要给每个gene一个初始representation。
  - 作者想研究用预训练 GeneCompass 的 gene embeddings 初始化这些 gene nodes会不会更好，相当于给跨物种图神经网络一个更好的初始 gene representation。

- Fig4 



```
                    GeneCompass gene embedding
                            │
           ┌────────────────┼────────────────┐
           ↓                ↓                ↓
        GRN推断         药物剂量响应      表达谱预测
                                            │
                                            ↓
                                      剂量敏感性预测
```
---


![pasted_1786279377845_xmzktb.png](https://pic1.imgdb.cn/i/03449umMtnpebpcBzRH0io.png)

- 做下游任务GRN

  - GRN实际上就是计算gene之间的余弦相似度提供先验
  - 然后 DeepSEM 本身再根据 scRNA-seq 表达数据学习最终 GRN

  - GRN inference 是一个严重类别不平衡任务，所以使用 AUPRC
  - ground truth based on ChIP-Seq，并与 PECA GRN prior knowledge 做了 de-duplication。作为验证的关系里面剔除了预训练的GRN关系

- 下游任务Drug dose response prediction

  - 药物剂量与基因表达反应之间的关系。
  - 用CPA这个模型做

- 下游任务Gene expression profiling

- Fig4都是结合其他模型做的，**同一套 GeneCompass 预训练 gene embeddings 能被四种完全不同的生物学任务利用，而且随着预训练数据增加，大多数任务的表现总体改善。**这个就是foundation model。



- Fig6

![pasted_1786281079101_iusz0s.png](https://pic1.imgdb.cn/i/0344Abrz3JHCDCfkfvyMMf.png)

这里和我们前面讲的 Fig. 2 非常不一样。Fig. 2 主要是**删掉一个 gene，看其他 gene embedding 怎么变**；Fig. 6 则是**定量改变 gene 的 expression，看整个 cell embedding 怎么移动**。

 GeneCompass 同时看到：


```
Expression变化
+
Ranking变化
```
---



所以一次过表达会同时改变这两个输入信息。

完整的一个流程：


```
① GeneCompass预训练时
同时学习Gene ID + expression + ranking

                ↓

② 人工修改某gene expression
比如：
过表达 / 降低一半 / 降到1/4 / 降到0

                ↓

③ 所有gene按照新的expression重新排名

                ↓

④ 把修改后的同一个cell
再次送入GeneCompass

                ↓

⑤ 得到新的cell embedding

                ↓

⑥ 比较：

原始cell embedding
扰动后cell embedding
目标cell embedding

                ↓

⑦ 如果扰动后：
离原始状态更远
离目标状态更近

说明这个gene可能推动目标cell fate

                ↓

⑧ 对ESC中的大量gene逐个模拟过表达

                ↓

⑨ 找出：
NR2F1
NR5A1
WT1
TCF21
GATA4

                ↓

⑩ 真实湿实验验证NR5A1和GATA4

                ↓

性腺相关marker上升
转录组改变
GO富集到gonadal processes
```
---



- 总结

研究者将基因相关的先验知识融入模型，整合了 101.8M 跨物种（人类+小鼠）单细胞数据，成功训练了 GeneCompass，一个能够、全面地理解复杂的基因调控网络的单细胞基座模型。总体而言，GeneCompass 的设计与研究体现了多方借鉴与优化的成果：输入序列融合了 Geneformer 和 scGPT 的设计思路，并创新性地加入了先验知识作为补充信息；代码实现上，直接沿用了 Geneformer 的框架并进行了改进；在下游应用上，几乎覆盖了目前单细胞基座模型的主要设计思录、数据集、和评估方法。这是一种兼具高效性与创新性的研究方法。

**此外，在跨物种创新设计上，仍有更广阔的探索空间**。通过混合人类和小鼠单细胞数据并注入同源基因信息的预训练模型，GeneCompass 在解决[药物研发](https://zhida.zhihu.com/search?content_id=250733522&content_type=Article&match_order=1&q=药物研发&zhida_source=entity)中的关键问题方面展现出巨大潜力。例如，药物研发初期通常以实验动物为模型进行筛选，但这种研发方法在人类中的[转化率](https://zhida.zhihu.com/search?content_id=250733522&content_type=Article&match_order=1&q=转化率&zhida_source=entity)极低。如果能够合理设计下游任务，让 GeneCompass 预测基因变化在小鼠和人类细胞间的一致性，将为提高药物研发的临床转化效率提供重要助力，对未来的[精准医学](https://zhida.zhihu.com/search?content_id=250733522&content_type=Article&match_order=1&q=精准医学&zhida_source=entity)与药物开发具有深远意义。