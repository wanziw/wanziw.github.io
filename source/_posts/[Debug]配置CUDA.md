---
title: 【Debug】配置CUDA
date: 2024-09-26 21:55:54
categories: bug解决日记
description: "torch.version.cuda"
tags: 深度学习
---




# 配置CUDA

cuda版本 根据pytorch选择

https://pytorch.org/get-started/locally/

https://pytorch.org/get-started/previous-versions/





[torch cuda 环境检测失败](https://blog.csdn.net/lvyuanj/article/details/139257068)

debug过程中遇到了一个弱智的错误，就是第一个有结果，后面两个都没有结果torch.version.cuda返回None，网上一般的说法是因为pytorch安装的是cpu版本，需要重新安装GPU版本。但是我分不清是我重新下载解决的这个bug，还是因为vscode里没有重启解决的，所以还是记录一下吧



```python
import torch

print(torch.__version__) # 查看torch版本
print(torch.cuda.is_available()) torch
print(torch.version.cuda)
```











