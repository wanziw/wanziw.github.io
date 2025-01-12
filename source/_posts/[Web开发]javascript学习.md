---
title: 'javascript学习'
date: 2025-01-12 16:39:10
categories: Web开发
cover: /img/cover21.jpg
tags: 
  - 前端
  - js
description: "web开发js学习笔记"
---

# JavaScript

[toc]

> b站视频：[四十分钟JavaScript快速入门 | 无废话且清晰流畅 | 手敲键盘 | WEB前端必备程序语言~](https://www.bilibili.com/video/BV15L4y1a7or)

# 1 浏览器开发者工具

![](https://pic1.imgdb.cn/item/67838149d0e0a243d4f39e99.png)

F12开发者工具 console里面可以敲js代码

# 2 搭建开发环境

下载vscode

下载nodejs

下载liveserver

# 3 使用script代码

引入第三方库可能使用

但是自己写的时候

\<script\>要写在body的末尾

因为浏览器是自上而下加载的，这样可以先把用户界面加载出来再加载js代码



一般我们想输入

```javascript
<script></script>
<h1></h1>
```

的时候，

输入script然后按tab键就好了

然后command/ctrl+D是重复前面步骤

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>test1</h1>
<script>
  console.log("这是第一句js代码")
</script>

</body>
</html>
```

# 4 编码原则之关注点分离

单独整一个js文件

然后在html里面引入





# 5 使用node运行js代码

终端输入

```bash
node --version
```





node是异步运行js的东西

# 6 变量和常量

```
var、let、const
```

var基本上不用

let可以重新赋值

const就不能变

通常推荐使用 `const` 来声明变量，只有在确实需要重新赋值时才使用 `let`。

# 7 原生数值类型





















