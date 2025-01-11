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

> 论文1提供了一个特征
>
> 论文2提供思路 先初步筛查然后再针对脓毒症特异性模型
>
> 论文3主要是讨论了PCT、NLR和CRP这三个特征
>
> 论文4研究意义很好，但是使用的文本数据也没啥用，作为一篇NC，讨论了大量的场景和技巧对比值得学习
>
> 论文5提供了多分类的一个思路，可以预测严重的患者和一般的患者
>
> 论文6没啥东西，主要就是在统计分析，参考指标可以看看这篇，模型非常简单，参考指标都是偏后期的了
>
> 论文7 之前的研究都是回顾性分析 这篇是前瞻性研究 对已经应用在医院里的用ML进行脓毒症早期预警系统的效果的总结  有较大参考价值

- [Developing an early warning system for detecting sepsis in patients with trauma](https://onlinelibrary.wiley.com/doi/10.1111/iwj.14652)
  - 2024的这篇文章，就用了一个多元逻辑回归，然后病人的数据基本都是已经比较问题大的病人了，采用的一些指标普通病人也没有，
  - 已读

- [Development and validation of an early warning tool for sepsis and decompensation in children during emergency department triage](https://www.nature.com/articles/s41598-021-87595-z)
  - 儿童脓毒症预警
  - 已读

- [Low serum thyroid-stimulating hormone levels may be an early predictor of sepsis](https://spcare.bmj.com/content/early/2022/12/07/spcare-2022-004027)
  - 血清促甲状腺激素水平低可能是脓毒症的早期预测指标
  - 已读
- Comparison of early warning scores for sepsis early identification and prediction in the general ward setting
  - https://journals.sagepub.com/doi/10.1177/1054773818823334
- [The Sepsis Score Dilemma: Balancing Precision and Utility](cation/384478209_The_Sepsis_Score_Dilemma_Balancing_Precision_and_Utility)
  - 脓毒症评分困境：平衡精度和效用
  - 已读
- [Early warning scores for sepsis identification and prediction of in-hospital mortality in adults with sepsis: A systematic review and meta-analysis](https://onlinelibrary.wiley.com/doi/10.1111/jocn.17061)
  - 已读
- [Artificial intelligence in sepsis early prediction and diagnosis using unstructured data in healthcare](https://nature.com/articles/s41467-021-20910-4)
  - 一篇NC
  - 已读
- [A sepsis early warning system is associated with improved patient outcomes](https://www.cell.com/cell-reports-medicine/fulltext/S2666-3791(22)00295-6)
  - 脓毒症早期预警系统与改善患者预后相关
  - 一篇spotlight
  - 已读
- [Prospective, multi-site study of patient outcomes after implementation of the TREWS machine learning-based early warning system for sepsis](https://www.nature.com/articles/s41591-022-01894-0)
  - 点评的是这篇论文
  - 没看

- [Prospective study and validation of early warning marker discovery based on integrating multi-omics analysis in severe burn patients with sepsis](https://academic.oup.com/burnstrauma/article/doi/10.1093/burnst/tkac050/6987826?login=true)
  - 这篇做了一个多组学的烧伤病人脓毒症预测，其实还有点意思，但是一般病人也不会测组学数据，更多的可能偏向机理研究，找一些靶点
  - 没看
- [Lessons in machine learning model deployment learned from sepsis](https://www.sciencedirect.com/science/article/pii/S2666634022003634)
  - 从脓毒症中吸取的机器学习模型部署经验教训
  - 这篇跟具体模型部署应用场景有关，应该挺有用的
  - 没看
- 论文4的refs有时间可以看一下

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

> scientific reports
>
> 这篇论文特别是针对儿童进行了模型设计，最好就是在急症科进行预警。
>
> 是进行了一个**多分类**的任务，提供了一个多分类任务的参考，如果要做严重程度的这个预警，可以参考这个，其实也就相当于是换了一个指标y，然后特征x没变
>
> 这篇研究认为特异性被认为比敏感性更为重要，就是要减少假阳性，然后为了补充漏检，引入了**实验室确认的菌血症**作为一种额外的响应变量y

[Development and validation of an early warning tool for sepsis and decompensation in children during emergency department triage](https://www.nature.com/articles/s41598-021-87595-z)

- 537,837条数据
  - 2013.3-2019.12的儿科数据
  - 483 名患者患有严重脓毒症和/或死亡
  - 1102 名患有非严重脓毒症
  - 1103 名菌血症检测呈阳性
  - 其余患者没有发生任何事件

- 模型
  -  multi-class的随机gradient boosting model 
  - 识别与死亡、严重脓毒症、非严重脓毒症和菌血症相关的早期预警信号 
  - 是个多分类的任务

- 特征
  - 生命体征、既往诊断、药物和指数 ED 就诊后 6 个月内的医疗保健使用情况
- 模型发现的重要的特征
  - 年龄、心率、既往住院时间、体温、收缩压和既往脓毒症

- 研究意义
  - 研究结果用于开发脓毒症的自动早期预警决策工具。在儿科急诊科实施该模型将允许在几秒钟的分诊后准确预测与脓毒症相关的严重失代偿。

## Method

每个患者是一个多类结果变量

>  （1） 使用全因死亡率过期的患者;
>
> （2） 患有严重脓毒症的患者;
>
> （3） 非重度脓毒症患者;
>
> （4） 菌血症试验阳性但未诊断为脓毒症的患者;
>
> （5） 未经历上述 4 种事件的患者。诊断代码（ICD-9-CM 和 ICD-10-CM）用于识别脓毒症患者，这有助于自动识别脓毒症





- 指标
  - https://www.nature.com/articles/s41598-021-87595-z/tables/1
  - https://www.nature.com/articles/s41598-021-87595-z/tables/2
  - 还有一些交互指标
    - 既往住院时间的最大值、脓毒症诊断、静脉注射药物、非局部抗生素和碳青霉烯类药物的病史。
    - 平均计算效应和与其他变量的**交互作用**，有较长住院时间、脓毒症、非局部抗生素和碳青霉烯类药物病史的患者发生严重或脓毒症相关失代偿的风险增加。

- 关于这个模型训练
  - **逐步多类分类**：这里的逐步多类分类策略是通过将每个类别作为一对多分类问题来处理的，即对每个类别单独进行二分类，然后基于这些二分类结果来计算最终的预测结果。每个类别的阈值选择会影响最终分类的结果。
  - **每个** y **的阈值不同**：每个 y（即每个类别）的预测阈值可能不同，特别是在类别不平衡的情况下。通过选择不同的概率阈值，可以优化模型的敏感性、特异性、阳性预测值等性能指标，并减少误分类的风险。这意味着，某些类别可能需要更高的特异性（减少假阳性），而其他类别可能更注重保持灵敏度（减少假阴性）。
  - **例如：**
    - 对“重度脓毒症”类别，可能选择较低的预测概率阈值，以确保不会漏掉任何重度脓毒症病例，保证较高的灵敏度。
    - 对“普通脓毒症”类别，可能选择较高的阈值，以避免误分类为脓毒症病例，从而增加特异性。

# 论文6：开发用于检测创伤患者脓毒症的早期预警系统

> 进行了统计分析，统计分析部分可以参考一下

[Developing an early warning system for detecting sepsis in patients with trauma](https://onlinelibrary.wiley.com/doi/10.1111/iwj.14652)

中国河北医科大学第三医院急诊科急诊重症监护室





# 论文7:脓毒症早期预警系统与改善患者预后相关

> 2018年就开始应用了，收集了两年的数据
>
> 告诉我们想法是可行的，然后针对他们实践中的问题我们可以针对性优化
>
> 这篇是点评的论文8

[A sepsis early warning system is associated with improved patient outcomes](https://www.cell.com/cell-reports-medicine/fulltext/S2666-3791(22)00295-6)
[Human–machine teaming is key to AI adoption: clinicians’ experiences with a deployed machine learning system](https://www.nature.com/articles/s41746-022-00597-7)

> - 关于具体实践
>   - https://www.nature.com/articles/s41746-024-01094-9?fromPaywallRec=false
>   - https://www.nature.com/articles/s41746-020-00367-3?fromPaywallRec=false

对于一个已经在基于机器学习（ML）的脓毒症早期预警系统（EWS）实际应用中



**1. 背景与问题**

- 脓毒症是全球住院和死亡的主要原因，但针对脓毒症的有效干预措施很少。尽早识别脓毒症并及时给药有助于提高生存率。
- 目前，脓毒症早期预警系统（EWS）作为一种干预工具，尤其在重症监护病房（ICU）中被广泛关注。
- 尽管许多EWS模型在回顾性研究中得到了验证，但在临床环境中的前瞻性评估相对较少。



**2. 研究设计与方法**

- 研究是前瞻性、多中心、双臂队列研究，旨在评估基于机器学习的脓毒症警报系统（TREWS）对患者结果的影响
- TREWS系统集成在电子健康记录（EHR）中，实时监测患者生命体征、实验室数据、药物医嘱和临床文档，从而生成脓毒症风险评分。
- 警报触发后，提供者可以选择确认或忽略警报。
- 研究纳入了2018年到2020年间五家医院590,736次住院就诊的记录，符合特定条件的6877例患者被纳入分析。



**3. 主要发现**

- **主要结局**：调整后的全因住院死亡率。研究发现，警报确认后3小时内的及时响应与较低的死亡率（14.6% vs 19.2%）相关，调整后的死亡风险差为-3.3%（p < 0.001）。
- **次要结局**：警报后72小时内SOFA评分和住院时间。研究显示，确认警报后的患者在SOFA评分和住院时间上有显著改善。
- SOFA评分的调整变化为-0.3分（p = 0.001）。
- 幸存者的住院时间缩短了11.6小时（p = 0.001）。



**4. 研究贡献与优势**

- 这是第一项前瞻性研究，证明了基于机器学习的脓毒症警报系统可以提前识别脓毒症患者，并有效改善患者的临床结果。
- 该研究具有多中心设计、较大样本量以及低监测偏倚风险等优势。

**5. 存在的问题与挑战**

- **提供者变异性**：虽然调整了患者层面的变异性，但提供者层面的变异性难以完全消除，可能影响警报响应和患者结果。
- **警报疲劳问题**：尽管警报系统触发了42,089次，但仅有13,680次满足脓毒症标准。进一步的工作需要在警报使用上减少“警报疲劳”。
- **技术扩展性**：虽然TREWS系统在五个站点成功实施，但在不同医院EHR系统中的实施仍存在挑战，需要进一步发展互操作性标准（如HL7和FHIR）来促进广泛应用。



**6. 未来方向**

- **随机化研究**：未来需要更多的随机化临床试验来进一步评估这种基于机器学习的系统。
- **技术与人因学研究**：需要深入研究推动提供者使用和反应的因素，以优化EWS系统的使用。
- **大规模实施**：随着EWS的普及，研究将聚焦于如何将其有效地部署到不同医院的EHR系统中，以确保其长期可行性。



**总结：**

**实时EWS**，如TREWS系统，通过实时监测患者状态并触发警报，有可能显著改善患者的预后，尤其是通过促进更早和更适当的临床干预。尽管存在一些技术和实施挑战，未来的工作将聚焦于进一步验证系统的效果，并克服这些挑战，以实现大规模的临床应用。



# 论文8:实施基于 TREWS 机器学习的脓毒症早期预警系统后患者预后的前瞻性多中心研究

> 模型用的比较简单、指标也比较简单
>
> 研究的比较早

[Prospective, multi-site study of patient outcomes after implementation of the TREWS machine learning-based early warning system for sepsis](https://www.nature.com/articles/s41591-022-01894-0)

取出了一个高危队列

主要是使用了**Cox比例风险模型的混合模型**，用于解释患者群体的异质性

用的模型是这两篇：

A targeted real-time early warning score (TREWScore) for septic shock

a targeted real-time early warning score (TREW score) for septic shock in a community hospital: global and subpopulation performance.

> 跟别的方法对比们可以看到都是很早的方法
>
> 与现有的修改早期预警评分（MEWS）相比，TREWScore的AUC值更高（MEWS为0.73）。
>
> 常规筛查协议（基于SIRS标准、感染怀疑、低血压或高乳酸血症）在灵敏度和特异性方面表现较差，灵敏度仅为0.74。



**Cox比例风险模型**

该模型被用来预测脓毒症的风险。每个组内的Cox比例风险模型使用患者的历史数据（如生命体征、药物使用史等）来计算脓毒症的风险。多个Cox模型组合成一个专家混合模型（mixture of experts model），每个模型输出一个风险值，并根据患者所在组的分配权重计算最终的预测风险值。

1. **模型训练和患者分组**

   - **混合模型**：通过患者的人口统计信息和健康历史，将患者分到一个或多个组。每个组内的数据用于学习该组的特定Cox比例风险模型。模型训练是**迭代的**，旨在同时优化患者的分组和每个组内的预测模型参数。

   - **分配和加权**：每个患者被分配到一个或多个模型，模型的输出结果（每个模型的风险值）会按照患者的分组权重进行加权平均，最终生成风险评分。

2. **输入数据**

   - TREWS使用的输入数据包括常规的实验室检测、生命体征、临床笔记、用药历史（不包括抗生素）、手术历史等。模型使用这些数据来训练Cox比例风险模型。与Henry等人报告的模型相比，TREWS模型做了几个扩展：

   - **数据来源**：Henry等人的模型仅使用ICU（重症监护病房）的数据，并专注于预测脓毒症休克。而TREWS使用来自整个医院的数据，包括急诊科、观察病房、普通病房和ICU。

   - **多模型组合**：TREWS不仅学习一个Cox比例风险模型，而是结合了多个模型，这通过混合模型来处理不同患者群体的异质性。

   - **额外特征**：根据与临床医生的讨论，TREWS模型加入了一些额外的特征，如麻醉品血液检查、输血医嘱和镇静剂，这些因素被认为是脓毒症的常见混杂因素。



## ref

1. Giannini, H. M. et al. A machine learning algorithm to predict severe sepsis and septic shock: development, implementation, and impact on clinical practice. *Crit. Care Med.* **47**, 1485–1492 (2019).
2. Desautels, T. et al. Prediction of sepsis in the intensive care unit with minimal electronic health record data: a machine learning approach. *JMIR Med. Inform.* **4**, 1–15 (2016).
3. Shashikumar, S. P., Josef, C. S., Sharma, A. & Nemati, S. DeepAISE—an interpretable and recurrent neural survival model for early prediction of sepsis. *Artif. Intell. Med.* **113**, 102036
4. Horng, S. et al. Creating an automated trigger for sepsis clinical decision support at emergency department triage using machine learning. *PLoS ONE* **12**, e0174708
5. Bedoya, A. D. et al. Machine learning for early detection of sepsis: an internal and temporal validation study. *JAMIA Open* **3**, 252–260 (2020).





# 论文9:基于整合多组学分析的重度烧伤脓毒症患者早期预警标志物发现的前瞻性研究与验证

>  从多组学的角度出发，拓展一下思维

![](https://pic1.imgdb.cn/item/677fbbe9d0e0a243d4f2c8a8.png)

**基因组学**: 对40例严重烧伤患者（NS组n=24，S组n=16）进行全外显子组测序（WES），筛选易感基因。

**miRNA组学**: 分析血浆中的miRNA，筛选差异表达的miRNA作为预警标志物。

**蛋白质组学**: 通过DIA和PRM技术筛选和验证差异蛋白。

**单细胞转录组学**: 对中性粒细胞进行单细胞转录组测序，探讨其在脓毒症中的作用。

**基因组学分析**:

- 筛选出26个易感基因，其中7个基因（DNAH11, LAMA2, ABCA2, ZFAND4, CEP290, MUC20, ENTPD1）在S组中突变频率显著高于NS组，可能增加脓毒症风险。

**miRNA组学分析**:

- 发现四种miRNA（hsa-miR-16-5p, hsa-miR-185-5p, hsa-miR-451a, hsa-miR-423-5p）可能作为烧伤相关脓毒症的早期预警标志物。

**蛋白质组学分析**:

- 筛选出两种候选蛋白（S100A8和SERPINA10）作为早期预警标志物。
- S100A8不仅是预警指标，还可能作为治疗靶点。

**单细胞转录组学分析**:

- 中性粒细胞在严重烧伤的发病机制中起重要作用，支持其在早期预警和治疗中的关键角色。

**动物实验验证**:

- 在小鼠烧伤模型中，S100A8显示出良好的早期预警能力和治疗效果。

> 我们对严重烧伤患者进行了一项多中心、前瞻性多组学研究，以筛查严重烧伤患者并发脓毒症的预防和治疗生物标志物。在基因水平上，发现重度烧伤患者脓毒症的 7 个易感基因： DNAH11 、 LAMA2 、 ABCA2 、 ZFAND4 、 CEP290 、 MUC20 和 ENTPD1。此外，我们确定了四种 miRNA （hsa-miR-16-5p、hsa-miR-185-5p、hsa-miR-451a 和 hsa-miR-423-5p），它们可能作为烧伤相关脓毒症的警告指标。在蛋白水平上，发现蛋白 S100A8 和 SERPINA10 是脓毒症严重烧伤患者的生物标志物，scRNA-seq 结果也揭示了中性粒细胞在严重烧伤早期的重要作用。此外，我们证实了中性粒细胞相关蛋白 S100A8 在严重烧伤相关脓毒症的早期预警和治疗中的作用。我们的研究为严重烧伤相关脓毒症的早期预警提供了良好的生物标志物，并为严重烧伤的早期治疗提供了良好的潜在临床治疗靶点。









