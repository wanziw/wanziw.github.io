---
title:  JQuery学习
date: 2025-01-13 11:52:20
categories: Web开发
cover: /img/cover22.jpg
tags: 
  - 前端
  - js
description: "web开发前端jquery学习笔记"
---

[toc]

> [3小时带你玩转jQuery+Ajax（前端开发-从入门到精通）](https://www.bilibili.com/video/BV19L4y1v7Dy)

# JQuery

![](https://pic1.imgdb.cn/item/67848ed1d0e0a243d4f3c97f.png)

jquery是一个js的脚本库，让js代码写的更加简洁

# 1 安装和下载

首先我们要选去jquery官网下载jquery，并将js脚本保存在指定位置

- 在页面中引入
  - **.min.js是压缩版，开发的时候传输更快，没有min的是完整学习的版本，有源码

```html
<script src="js/jquery-3.4.1.js" type="text/javascript"></script>
```

- jquery核心
  - `$` 符号在 jQuery 中代表对 jQuery 对象的引用，`jQuery` 是核心对象。
- 通过该对象可以获取 jQuery 对象，调用 jQuery 提供的方法等。

- **只有** jQuery 对象才能调用 jQuery 提供的方法。



# 2 Dom对象和jquery包装集对象

通过js代码获取的对象都是dom对象，通过jquery获取的对象都是jquery包装集对象，对象的属性和方法要多得多

> 原始的 DOM 对象只有 DOM 接口提供的方法和属性，通过 JavaScript 代码获取的对象都是 DOM 对象；而通过 jQuery 获取的对象是 jQuery 包装集对象，简称 jQuery 对象，只有 jQuery 对象才能使用 jQuery 提供的方法。

## 2.1 DOM 对象

在 JavaScript 中获取 DOM 对象时，DOM 对象只有有限的属性和方法，例如：

```javascript
var div = document.getElementById("div");
var divs = document.getElementsByTagName("divtext");
```

## 2.2 jQuery 包装集对象

jQuery 对象可以看作是对 DOM 对象的扩展。在 jQuery 的世界中，所有的对象，无论是单个元素还是一组元素，都会被封装成一个 jQuery 包装集。例如，获取包含一个元素的 jQuery 包装集：

```javascript
var jQueryObject = $("#testdiv");
```



- 引入js文件

```html
{% load static %}

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>test1</h1>
<div id="mydiv"> 文本 </div>
{#<script src="{% static "js/test1.js"%}"></script>#}
<script src="{% static "js/core.min.js"%}"></script>
<script src="{% static "js/script.js"%}"></script>
</body>
<script type="text/javascript">
    //dom对象
    var domDiv = document.getElementById("mydiv")
    console.log(domDiv)  //单个

    var domsDiv = document.getElementsByTagName("div")
    console.log(domsDiv) //数组

    // jquery对象
    // 通过id选择获取元素对象 $("#元素id")
    var divJquery = $("#mydiv")
    console.log(divJquery)

</script>
</html>
```

- 打印结果

![](https://pic1.imgdb.cn/item/67849657d0e0a243d4f3ca71.png)

前两个是dom，最后一个是jquery对象



用原生js去获取一个不存在的元素对象的时候，返回的是null

用jquery这样去获取的话，是返回一个空的jquery对象

## 2.3 DOM对象转jquery对象

将 DOM 对象转换为 jQuery 对象，只需要利用 `$()` 方法进行包装即可：

```javascript
var domDiv = document.getElementById('mydiv'); // 获取 DOM 对象
var jQueryDiv = $(domDiv); // 转换为 jQuery 对象
```

## 2.4 jQuery 对象转 DOM 对象

jQuery 对象转 DOM 对象，只需要取数组中的元素即可。以下是两种获取 jQuery 对象的方式及其转换为 DOM 对象的方法：

```javascript
// 第一种方式 获取 jQuery 对象
var jqueryDiv = jQuery('#mydiv');

// 第二种方式 获取 jQuery 对象
var jqueryDiv = $('#mydiv');

// 将获取的 jQuery 对象转为 DOM 对象
var domDiv = jqueryDiv[0];
```

# 3 Jquery选择器



和使用 JavaScript 操作 DOM 一样，获取文档中的节点对象是一个非常频繁的操作。在 jQuery 中，提供了简便的方式供我们查找和定位元素，称为 **jQuery 选择器**。选择器可以说是最考验一个人 jQuery 功力的地方，通俗地讲，选择器就是“一个表示特殊语义的字符串”。只要将选择器字符串传入相关的方法中，就能够选择不同的 DOM 对象，并且以 jQuery 包装集的形式返回。



jQuery 选择器按照功能主要分为“选择”和“过滤”，并且是配合使用的，具体分类如下。基础选择器掌握即可，其他用到时再查阅。



## 3.1 基础选择器

主要是掌握前三个，用的比较多

- `$("#id属性值")`
  - 选择 ID 为指定值的元素对象（如果有多个相同的 ID，选择第一个匹配的元素）。

- `$(".class属性值")`
  - 选择类名为指定值的所有元素对象。

- `$("标签名/元素名")`
  - 选择所有指定标签名的元素对象。
  - 比如div



- `$("*")`
  - 选择页面中所有的元素对象。

- `$("选择器1, 选择器2, …")`
  - 选择符合任一选择器的元素对象。

## 3.2 层次选择器



| **选择器类型** | **名称**            | **语法**                    | **描述**                           | **示例**             |
| -------------- | ------------------- | --------------------------- | ---------------------------------- | -------------------- |
| **后代选择器** | ancestor descendant | `$("#ancestor descendant")` | 选择祖先元素内部的所有后代元素。   | `$("#parent div")`   |
| **子代选择器** | parent > child      | `$("#parent > child")`      | 选择指定父元素的直接子元素。       | `$("#parent > div")` |
| **相邻选择器** | prev + next         | `$(".prev + next")`         | 选择紧接在指定元素之后的相邻元素。 | `$(".blue + img")`   |
| **同辈选择器** | prev ~ sibling      | `$(".prev ~ sibling")`      | 选择在指定元素之后的所有同级元素。 | `$(".blue ~ img")`   |





## 3.3 表单选择器



