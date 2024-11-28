
---
title: Overleaf学习
date: 2024-10-25 20:14:30 
cover: /img/cover1.jpg
categories: 科研工具
tags: 论文写作

---

# Overleaf学习

[【论文写作】使用overleaf撰写你的会议论文](https://blog.csdn.net/m0_37201243/article/details/120170141)


# 要点
- 中间空一行就是分段

## 分节

- \section{introduction}
- \subsection{}

## 公式

```tex
\begin{equation}
a+b=\gamma\Label{eq}
\end{equation}
```

## 表格

```tex
\begin{table}
\end{table}
```

表格中间的内容可以利用一些在线网站生成

```tex
\begin{table}
  \caption{Frequency of Special Characters}
  \label{tab:freq}
  \begin{tabular}{ccl}
    \toprule
    Non-English or Math&Frequency&Comments\\
    \midrule
    \O & 1 in 1,000& For Swedish names\\
    $\pi$ & 1 in 5& Common in math\\
    \$ & 4 in 5 & Used in business\\
    $\Psi^2_1$ & 1 in 40,000& Unexplained usage\\
  \bottomrule
\end{tabular}
\end{table}
```

## 图片

一般项目会创建一个文件夹叫做figure用来存图片



```tex
\begin{figure}[h]
  \centering
  \includegraphics[width=\linewidth]{sample-franklin}
  \caption{1907 Franklin Model D roadster. Photograph by Harris \&
    Ewing, Inc. [Public domain], via Wikimedia
    Commons. (\url{https://goo.gl/VLCRBB}).}
  \Description{A woman and a girl in white dresses sit in an open car.}
\end{figure}
```





# 参考文献

zotero下载插件 better bibtex

zotero  

- 右键文件夹->导出 BibTex格式->生成bib文件并命名

Overleaf

- 上传bib文件到overleaf项目里
- 主文件最后输
  - 假设文件叫做myreference.bib
  - `\bibliographystyle{plain}`
    - 定义style，比如让参考文献按照首字母排序还是引用顺序排序
    - 一般期刊会给个cls文件来定义这些
  - `\bibliography{myreference}`
- 文章中插入引用
  - \cite{}
  - 可以选择
- 期刊对引用文献的要求
  - 在zetero首选项里打开better bibtex
    - “导出”->"字段" 
    - 对不导出的部分，我们进行删除就行 