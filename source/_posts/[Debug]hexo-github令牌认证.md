---
title: 【Debug】hexo-github令牌认证
date: 2024-07-19 14:40:54
categories: bug解决日记
description: "Support for password authentication was removed on August 13, 2021."
cover: https://pic.imgdb.cn/item/669b38ebd9c307b7e9f3e5e0.jpg
---

# 第一章

第一篇博客记录一下hexo搭建过程中的bug

- 原本在hexo d之后的报错

```
(base) xuan@wangzixuandeMacBook-Pro BlogFile % hexo d
（省略。。）
Username for 'https://github.com': wanziw
Password for 'https://wanziw@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/wanziw/wanziw.github.io.git/'
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
```

根据问题发现是要创建令牌（token），在输入密码的部分要输入token

[Git The requested URL returned error: 403，Token authentication requirements for Git operations](https://blog.csdn.net/weixin_45844049/article/details/123733065)

- 结果创建完之后报错如下

```
fatal: unable to access 'https://github.com/wanziw/wanziw.github.io.git/': The requested URL returned error: 403
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html

```



解决方案：

发现创建错了，我创建成上面那个Fine-grained的了，其实应该创建下面那个

![](https://pic.imgdb.cn/item/669a0b5ad9c307b7e9bb84bc.png)

这玩意过期expired也会报这个bug
参考链接：https://www.jianshu.com/p/d5f2e04a332f