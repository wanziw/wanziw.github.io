
---
title: RNN实战
date: 2024-10-22 15:44:50
cover: https://pic.imgdb.cn/item/671b50c6d29ded1a8ce9a42e.png
categories: 深度学习
tags: 深度学习
description: 回顾RNN和LSTM
Copyright: true
copyright_author: wanzi
copyright_author_href: https://github.com/wanziw
copyright_url: https://wanziw.github.io/2024/10/22/%5B深度学习%5DRNN实战/

copyright_info: 此文章版權歸wanzi所有，如有轉載，請註明來自原作者

---

https://www.bilibili.com/video/BV1dZ4y1g7DE
# RNN

## 向量编码

- 第一种编码方式：onehot编码

> 一句话 5个词 有3500个不同的单词 每个词使用onehot编码，那么就是这句话的向量就是[5,3500]
>
> 类比到ATCG上面，一串序列长度为200，onehot编码之后向量就是[200,4]

![](https://pic.imgdb.cn/item/672f4af6d29ded1a8c7b3b22.png)



- 第二种编码方式
  - onehot编码往往太稀疏了
  - 所以一般是使用词向量，给词做embedding，在一个词向量空间中，每个词有自己的位置，语义相近的空间中距离近

![](https://pic.imgdb.cn/item/672f4bebd29ded1a8c7c6854.png)



### batch

我们深度学习的时候一般不是一次一个句子，而是一次多个句子训练。一批就是一个batch

- 对于CNN来说
  - 一个batch表示为[b,c,H,W]
- 对于RNN来说
  - [word num,b,word vec] ：训练的时候更像是这种
    - 看下面这个图，word num就是seq length，按照时间步进行一个一个的迭代，每一个向量是[batch,embedding_dim]
  - [b,word num,word vec]
    - batch放在前面更符合大家深度学习一般的操作
  - 用哪种只要在pytorch里设置一下就行

![](https://pic.imgdb.cn/item/672f4c9cd29ded1a8c7d3afe.png)

## 查embedding

![](https://pic.imgdb.cn/item/672f4e9ad29ded1a8c7fbe35.png)

对于单词来说，一般有做好的embedding表（比如word2vec/glove）。然后根据每个单词的索引我们去这个embedding表里面找词的向量表示

对于基因来说，我们一般是k-mer表示，不同的k-mer让他在空间中有一个不同的embedding值

- nn.embedding层
  - 这里这层设置为(2,5)，表示一次2个词，embedding_dim为5
  - 这个层的输入是索引，输出是embedding值

- 比如对于glove这个词表的使用
  - ![](https://pic.imgdb.cn/item/672f51b5d29ded1a8c837071.png)

# 循环神经网络原理



![](https://pic.imgdb.cn/item/672f8161d29ded1a8cb23a36.png)

![](https://pic.imgdb.cn/item/67304bbcd29ded1a8c38468c.png)





# RNN layer使用

假设这里hidden_len 是20

- 这样的memory单元一直传递

![](https://pic.imgdb.cn/item/67305bd4d29ded1a8c45b101.png)

- input dim ，hidden dim

```python
import torch
import torch.nn as nn

# 定义RNN
# 100是word_embedding_dim 10是memory_dim
rnn = nn.RNN(100, 10)

# 查看RNN的参数
rnn._parameters.keys()
# 输出：odict_keys(['weight_ih_l0', 'weight_hh_l0', 'bias_ih_l0', 'bias_hh_l0'])

# 检查权重的形状
print(rnn.weight_hh_l0.shape, rnn.weight_ih_l0.shape)
# 输出：(torch.Size([10, 10]), torch.Size([10, 100]))

# 检查偏置的形状
print(rnn.bias_hh_l0.shape, rnn.bias_ih_l0.shape)
# 输出：(torch.Size([10]), torch.Size([10]))

```

## nn.RNN

- x [seq_len,batch,vec_dim] h[b,hid_dim]
- h就是memory， hidden_dim就是memory_dim 一个意思

- nn.RNN(vec_dim,hid_dim,num_layers)

- \_init\_
  - **input_size**: 输入 \( x \) 的特征数，即每个输入向量的维度。
  - **hidden_size**: 隐藏状态 \( h \) 中的特征数，即隐藏层的维度。
  - **num_layers**: 循环层的数量。比如，设置 `num_layers=2` 会堆叠两个RNN层，形成一个堆叠的RNN，第二个RNN会接收第一个RNN的输出并计算最终结果。默认值为 1。

- Out,ht = forward(x,h0)

  - **x**: 输入张量，形状为[seq_len,b,word_vec]

  - **ho / ht**: 初始或最终的隐藏状态，形状为[num_layers,b,h_dim]

  - **out**: RNN的输出张量，形状为 [seq_len,b,h_dim]

  - > 根据这个图可以看到，ht是时间步的最后一个隐藏状态，out是每个时间步的输出汇总起来的

![](https://pic.imgdb.cn/item/673060ddd29ded1a8c4950e9.png)

### single layer RNN

一层的循环神经网络

```python
import torch
import torch.nn as nn

# 定义RNN
rnn = nn.RNN(input_size=100, hidden_size=20, num_layers=1)
print(rnn)

# 输入张量x的形状为 [seq_len, batch_size, input_size]
x = torch.randn(10, 3, 100)

# 初始化隐藏状态 h0 的形状为 [num_layers, batch_size, hidden_size]
h0 = torch.zeros(1, 3, 20)

# 运行RNN，得到输出和最终的隐藏状态
out, h = rnn(x, h0)

# 输出 out 和 h 的形状
print(out.shape, h.shape)

```

![](https://pic.imgdb.cn/item/6730631ad29ded1a8c4aef1f.png)

- 假设这里三句话，每句十个单词，每个单词的embedding是100维，输入x就是[10,3,100]
  - 假设中间隐藏层h的dim是20层，单层的RNN layer
    - h维度就是[1,3,20]
- out是总体的输出，所以是每个时间步的h输出加起来，就是[10,3,20]
  - 最后还需要接全连接层从20的dim还原到100

> 在我现在生信课题上面，一个序列长为200,dim为atcg 4，假设batch是64，那么就是[200,64,4]
>
> 中间的hidden_dim假设是[1,64,2] ，out是[200,64,2]

### Multi layers RNN

out状态不会变，h会变，out只会取最上面那层的状态

![](https://pic.imgdb.cn/item/67306868d29ded1a8c4f3898.png)



![](https://pic.imgdb.cn/item/6730687cd29ded1a8c4f4d7c.png)



## nn.RNNCell

跟nn.RNN的区别就是比如[10,3,100]的数据。RNN是循环对[3,100]进行了10次时间步的循环，RNNCell就是没有循环，让你单独执行一次步骤

![](https://pic.imgdb.cn/item/6730698bd29ded1a8c506d7e.png)

中间不是ht而是xt

![](https://pic.imgdb.cn/item/67306a90d29ded1a8c51396b.png)

# RNN代码实战

- 这里设置的是batch作为第一个参数
- 网络结构

![](https://pic.imgdb.cn/item/67306db7d29ded1a8c539d60.png)

- 训练过程

![](https://pic.imgdb.cn/item/67306e7ed29ded1a8c543f88.png)

- predict
- 









单向RNN主要是包含过去的信息

双向RNN 可以同时获取过去和未来的信息



![](https://pic.imgdb.cn/item/66f66a65f21886ccc0f00f97.png)

每一个$h_{t}$都是由前一刻的$h_{t-1}$和此刻的输入$x_{t}$的线性变换组成

向量长度是hidden_size 维度是input_size

batch_first 默认是False 打开之后数据格式就是（batch seq feature）

![](https://pic.imgdb.cn/item/66f673aff21886ccc0fa48bd.png)

比如这里batchsize是1，然后序列长度是2，维度（特征数）是3