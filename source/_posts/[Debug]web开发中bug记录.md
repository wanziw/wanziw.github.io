---
title: 【Debug】web开发过程中bug记录
date: 2025-02-23 17:56:54
categories: bug解决日记
description: "web开发中的bug记录，有些真的让人很无语！！"
cover: /img/cover30.jpg
tags: 后端
---

> web开发虽然是个debug的过程
> 但是有些bug还是过于无语了
> 记录在这里防止苯人再犯

# 1 提交注册一直跳转回登录界面

真的很无语。。原因是设置了`中间件`所以导致只能访问/login，没办法访问/register
```python
 no_auth_required = [
            "/zjbioinformatics/login/",
            "/zjbioinformatics/admin/login/",
            "/zjbioinformatics/register/",
            "/zjbioinformatics/image/code/"
        ]
```