---
title: sepsis论文阅读
date: 2025-01-07 13:04:56
categories: 论文阅读
cover: /img/cover15.jpg
tags: 
  - sepsis
description: "脓毒症预警系统相关论文"
---

[toc]



# 脓毒症

- [Developing an early warning system for detecting sepsis in patients with trauma](https://onlinelibrary.wiley.com/doi/10.1111/iwj.14652)

2024的这篇文章，就用了一个多元逻辑回归，然后病人的数据基本都是已经比较问题大的病人了，采用的一些指标普通病人也没有，

- [**Prospective study and validation of early warning marker discovery based on integrating multi-omics analysis in severe burn patients with sepsis**](https://academic.oup.com/burnstrauma/article/doi/10.1093/burnst/tkac050/6987826?login=true)

这篇做了一个多组学的烧伤病人脓毒症预测，其实还有点意思，但是一般病人也不会测组学数据，更多的可能偏向机理研究，找一些靶点

- [Lessons in machine learning model deployment learned from sepsis](https://www.sciencedirect.com/science/article/pii/S2666634022003634)

- [Development and validation of an early warning tool for sepsis and decompensation in children during emergency department triage](https://www.nature.com/articles/s41598-021-87595-z)

儿童脓毒症预警

- [Sepsis Screening: Combining Early Warning Scores and SIRS Criteria]()

- [Low serum thyroid-stimulating hormone levels may be an early predictor of sepsis](https://spcare.bmj.com/content/early/2022/12/07/spcare-2022-004027)
  - 血清促甲状腺激素水平低可能是脓毒症的早期预测指标

- Comparison of early warning scores for sepsis early identification and prediction in the general ward setting
  - https://journals.sagepub.com/doi/10.1177/1054773818823334

- [The Sepsis Score Dilemma: Balancing Precision and Utility](cation/384478209_The_Sepsis_Score_Dilemma_Balancing_Precision_and_Utility)
  - 脓毒症评分困境：平衡精度和效用

- A sepsis early warning system is associated with improved patient outcomes
  - 脓毒症早期预警系统与改善患者预后相关
- [Early warning scores for sepsis identification and prediction of in-hospital mortality in adults with sepsis: A systematic review and meta-analysis](https://onlinelibrary.wiley.com/doi/10.1111/jocn.17061)
- [Artificial intelligence in sepsis early prediction and diagnosis using unstructured data in healthcare](https://nature.com/articles/s41467-021-20910-4)
  - 一篇NC

- 



# 论文1:血清促甲状腺激素可能是脓毒症的早期指标

> TSH、T3/T4比率

[Low serum thyroid-stimulating hormone levels may be an early predictor of sepsis](https://spcare.bmj.com/content/early/2022/12/07/spcare-2022-004027)

这项研究的目的是看看 **促甲状腺激素（TSH）** 是否可以在细菌感染进展为 **脓毒症**之前，提前发出预警信号。

- cohort：2021.1.1-2021.8.31 北京朝阳医院急诊科 细菌感染的62个患者
- 分组：
  - **脓毒症组（SG）**：在入院后的72小时内病情发展为脓毒症的患者
  - **非脓毒症组（NSG）**：在入院后的72小时内病情未发展为脓毒症的患者
- 数据
  - 入院时进行的常规血液检查
  - 生化指标和甲状腺功能指标，包括 T4、FT4、T3、FT3
  - TSH水平
  - 评估患者的急性生理学和慢性健康评估 II（APACHE II）评分，以及序贯器官衰竭评估（SOFA）评分，这些评分用于评估患者的整体健康状况和器官功能。

- 结果
  - 实验组和对照组在TSH上有显著差异
- 就用了最简单的统计分析来研究了一下什么指标跟这两个相关

- 机制解释
  - 甲状腺激素（T3和T4）
  - 甲状腺激素调节炎症反应
  - **T3/T4比率下降**

# 论文2:脓毒症识别和早期预警评分

> qSOFA是什么
>
> 一篇review，写的有点让人看不懂。
>
> 反正就是比较了EWS、qSOFA≥2和SIRS≥2在预测脓毒症院内死亡率方面的准确性
>
> 这篇提供了一个好的观点，就是可以先初步筛查，假阳性高没事，筛选出来了再用专门针对sepsis的模型

[Early warning scores for sepsis identification and prediction of in-hospital mortality in adults with sepsis: A systematic review and meta-analysis](https://onlinelibrary.wiley.com/doi/10.1111/jocn.17061)

sepsisi-3定义，减少了对炎症反应（如SIRS）的依赖，因为研究发现SIRS缺乏特异性，容易导致误诊。

**qSOFA**：作为替代，快速序贯器官衰竭评估（qSOFA）评分被提出。qSOFA使用三个简单的临床参数：收缩压、精神状态和呼吸频率，来评估患者是否可能发展为脓毒症。

但是qSOFA灵敏度低、容易漏诊、发现的时候也已经晚了

这个研究比较了SIRS、qSOFA和EWS（早期预警评分）

- 结论：
  - EWS在预测脓毒症诊断方面的敏感性和特异性介于qSOFA和SIRS之间。
  - EWS在DOR和预测能力上优于SIRS，且避免了qSOFA的低敏感性问题。
  - **高敏感性对于脓毒症筛查工具更为重要，因为漏诊的后果更为严重**
- EWS不依赖实验室数据，更适合快速筛查
- 但是**均不是理想的独立脓毒症筛查工具**
- 建议是：
  - **分阶段筛查**：
    - 首先使用EWS筛查所有病例，识别需要更高水平护理的患者，然后使用更脓毒症特异性的工具进行进一步评估。
  - **结合其他风险因素或生物标志物**：
    - EWS可与其他临床风险因素或床旁生物标志物结合，提高筛查准确性。

# 论文3:脓毒症评分困境-平衡精度和效用

> PCT、NLR和CRP虽然在临床中常用，但并非理想的脓毒症生物标志物，尤其是CRP对全身炎症和脓毒症无法区分
>
> 这里主要是给印度专门开发了一个模型
>
> 也不是早期识别
>
> 

[The Sepsis Score Dilemma: Balancing Precision and Utility](cation/384478209_The_Sepsis_Score_Dilemma_Balancing_Precision_and_Utility)

**人群异质性**：脓毒症人群在地理位置、涉及的微生物、感染部位和免疫反应等方面具有相当大的异质性

## 评分指标

- 对于脓毒症的预测和严重情况量化有这些指标
- icu里
  - SOFA
  - SIRS
  - 简化急性生理评分III（SAPS III）
  - 脓毒症预测模型（SPM）
  - Moreno PIRO（易感性、损伤、反应和器官功能障碍）
  - 逻辑器官功能障碍评分系统（LODS）
  - 牛津急性病情严重度评分（OASIS）
- icu外
  - 创伤性脓毒症评分（TSS）
  - 早期预警评分
    - qSOFA：快速SOFA由于其表现低于早期报告的水平，并且低估了免疫功能低下患者的风险和不良结局，现已被放弃
    - 通用生命评估评分（UVAS）
    - 国家早期预警评分（NEWS）
    - 改良早期预警评分（MEWS）

> **常用评分工具**：
>
> - **SOFA**：评估器官功能障碍的严重程度，广泛用于ICU。
> - **SIRS**：基于体温、心率、呼吸频率和白细胞计数，用于早期识别脓毒症。
> - **SAPS III、SPM、PIRO、LODS、OASIS**：各种评分系统，用于不同环境下的脓毒症评估。
>
> **特定评分工具**：
>
> - **TSS**：用于创伤性脓毒症的评估。
> - **qSOFA**：快速评估工具，基于收缩压、呼吸频率和意识状态。
> - **NEWS和MEWS**：早期预警评分，用于识别病情可能急剧恶化的患者。



## 生物标志物

研究人员试图通过各种生物标志物（如PCT、CRP、D-二聚体、乳酸、细胞因子等）来提高脓毒症的检测和死亡率预测的准确性。

**PCT不被推荐用于脓毒症诊断或指导抗菌治疗**

## 结论

这篇文章主要是对ICU里面脓毒症的死亡率预测

使用多重逻辑回归分析生物标志物、临床评分与院内死亡率之间的关系，并通过自助法和净重新分类指数（NRI）评估预测性能

**目前的一些研究局限性**：

- **生物标志物选择**：PCT、NLR和CRP虽然在临床中常用，但并非理想的脓毒症生物标志物，尤其是CRP对全身炎症和脓毒症无法区分。
- **标志物敏感性和特异性**：许多生物标志物（如NLR、NPR、NMR）的敏感性和特异性较低，影响预测准确性。
- **数据损失**：研究中有较大比例的数据丢失（PCT 29.2%、CRP 9.9%、NLR 2.9%），可能影响模型的准确性。
- **样本量和多中心验证**：该研究为单中心研究，仅有170名患者，需要在更大规模、多中心的数据库中进行验证。
- **人工智能的应用**：AI在脓毒症早期检测和死亡率预测中显示出潜力，如SERA算法和“In Sight”机器学习算法，能提高预测准确性并减少假阳性。



# 论文4:人工智能在脓毒症中的早期预测和诊断在医疗保健中使用非结构化数据

> meta-analysis study是什么： Islam, M. M. et al. Prediction of sepsis patients using machine learning approach: a meta-analysis. *Comput. Methods Prog. Biomed.* **170**, 1–9 (2019).
>
> 这篇用的指标没有我们的多，只是短期预测的话，文本没啥价值
>
> 这篇论文测试了很多不同的场景和模型方法技巧对比值得我们学习
>
> 减少假阳性，不然会浪来了
>
> 意义跟我们一样

[Artificial intelligence in sepsis early prediction and diagnosis using unstructured data in healthcare](https://nature.com/articles/s41467-021-20910-4)

这篇文章跟我们的需求比较像

然后还使用了文本挖掘，医生的临床笔记来预测

预测这些患者在接下来的 4 、 6 、 12 、 24 和 48 小时内患脓毒症的风险

240个患者其中87为脓毒症患者，根据实践、发作时间为进入Icu的时间





- 数据不平衡问题
  - 合成少数过采样技术 （SMOTE） 来实现脓毒症病例和非脓毒症对照 （在临床记录水平） 的 1：1 平衡数据。
- 为了进行比较，我们还开发、测试和报告了**没有任何过采样**的模型，以提出在脓毒症患病率相对较低的正常临床环境中操作该算法的可能性。
- 都测试了这俩模型，结果只描述了SMOTE模型的结果

![](https://pic1.imgdb.cn/item/677d501bd0e0a243d4f17a8e.png)

- 结构数据

![](https://pic1.imgdb.cn/item/677d4fc1d0e0a243d4f17a4b.png)

- 非结构性的数据

采用LDA，生成主题词做文本挖掘

- 集成：dagging 和 gradient boosted trees （GBT） 

- 因变量：接下来的 4 、 6 、 12 、 24 和 48 小时内是否会出现脓毒症

## 结论

短期的没啥用

在这种情况下，临床文本的增加使用仅为 SERA 算法提供了边际预测增益，因为结构化变量捕获了大多数脓毒症症状。然而，当我们专注于脓毒症前 12 至 48 小时之间的早期预测时，非结构化临床文本提供了更大的预测价值，因为患者尚未表现出可以通过结构化脓毒症变量测量的可观察症状。

如果可以设计类似于 SERA 算法的预测算法来持续访问有价值的结构化和非结构化数据患者数据，那么医院系统就有可能提供 24 x 7 全天候持续监测患者病情，从而提高早期脓毒症检测和干预的能力。尽管与一些医生的诊断和之前的机器学习算法相比，SERA 算法可以实现更高的灵敏度和特异性，但我们认为它的主要作用是补充而不是替代临床团队的现有工作。我们进一步认为，可以开发其他类似的支持 NLP 的算法来增强医护人员的知识并改善他们的决策

## ref

- Horng, S. et al. Creating an automated trigger for sepsis clinical decision support at emergency department triage using machine learning. *PloS ONE* **12**, e0174708 (2017).
- Liu, R., Greenstein, J. L., Sarma, S. V., & Winslow, R. L. Natural language processing of clinical notes for improved early prediction of septic shock in the ICU. In *Proc. 41st Annual International Conference of the IEEE Engineering in Medicine and Biology Society*, 6103–6108 (2019).
- Lukaszewski, R. A. et al. Presymptomatic prediction of sepsis in intensive care unit patients. *Clin. Vaccine Immunol.* **15**, 1089–1094 (2008).
- Thiel, S. W. et al. Early prediction of septic shock in hospitalized patients. *J. Hosp. Med.* **5**, 19–25 (2010).
- Shashikumar, S. P. et al. Early sepsis detection in critical care patients using multiscale blood pressure and heart rate dynamics. *J. Electrocardiol.* **50**, 739–743 (2017).
- Nemati, S. et al. An interpretable machine learning model for accurate prediction of sepsis in the ICU. *Crit. Care Med.* **46**, 547–553 (2018).

# 论文5:儿童脓毒症预警

[Development and validation of an early warning tool for sepsis and decompensation in children during emergency department triage](https://www.nature.com/articles/s41598-021-87595-z)

