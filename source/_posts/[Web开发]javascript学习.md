---
title: 'javascript学习'
date: 2025-01-12 16:39:10
categories: Web开发
cover: /img/cover21.jpg
tags: 
  - 前端
  - js
description: "web开发前端js学习笔记"
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

```
string,number,boolean,null,undefined
```



建议声明变量最后都是用分号

```javascript
const username = "John";
const age = 30;
const rate = 4.5;
const isCool = true;
const x = null;
const y = undefined;
let z;
```

null表示存了一个空值，undefined表示没有定义是什么类型

`let a;`和`const obj = {};`就是undefined

`console.log(typeof username)`可以打印变量的类型

# 8 模版字符串

![](https://pic1.imgdb.cn/item/6783b5f8d0e0a243d4f3ab0d.png)



# 9 字符串的内置方法

| **方法名**                          | **示例**                                              | **意义**                               |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| `charAt(index)`                     | `"Hello".charAt(1)` → `"e"`                           | 返回指定索引位置的字符                 |
| `includes(sub)`                     | `"Hello World".includes("World")` → `true`            | 判断字符串是否包含指定子字符串         |
| `indexOf(sub)`                      | `"Hello".indexOf("e")` → `1`                          | 返回子字符串首次出现的位置             |
| `lastIndexOf(sub)`                  | `"Hello".lastIndexOf("l")` → `3`                      | 返回子字符串最后一次出现的位置         |
| `slice(start, end)`                 | `"Hello".slice(1, 4)` → `"ell"`                       | 提取字符串的一个片段                   |
| `substring(start, end)`             | `"Hello".substring(1, 4)` → `"ell"`                   | 类似 `slice`，但不支持负值索引         |
| `toLowerCase()`                     | `"HELLO".toLowerCase()` → `"hello"`                   | 将字符串转换为小写字母                 |
| `toUpperCase()`                     | `"hello".toUpperCase()` → `"HELLO"`                   | 将字符串转换为大写字母                 |
| `trim()`                            | `"  Hello  ".trim()` → `"Hello"`                      | 移除字符串两端的空白字符               |
| `split(separator)`                  | `"a,b,c".split(",")` → `["a", "b", "c"]`              | 根据分隔符将字符串拆分为数组           |
| `replace(search, replace)`          | `"Hello World".replace("World", "JS")` → `"Hello JS"` | 替换字符串中的指定部分                 |
| `includes()`                        | `"JavaScript".includes("Script")` → `true`            | 检查是否包含某个子字符串               |
| `startsWith(sub)`                   | `"Hello".startsWith("He")` → `true`                   | 判断字符串是否以指定子字符串开头       |
| `endsWith(sub)`                     | `"Hello".endsWith("lo")` → `true`                     | 判断字符串是否以指定子字符串结尾       |
| `concat(str)`                       | `"Hello".concat(" ", "World")` → `"Hello World"`      | 连接两个或多个字符串                   |
| `repeat(count)`                     | `"Hi! ".repeat(3)` → `"Hi! Hi! Hi! "`                 | 重复字符串指定次数                     |
| `padStart(targetLength, padString)` | `"5".padStart(3, "0")` → `"005"`                      | 在字符串开头填充指定字符以达到目标长度 |
| `padEnd(targetLength, padString)`   | `"5".padEnd(3, "0")` → `"500"`                        | 在字符串结尾填充指定字符以达到目标长度 |
| `match(regexp)`                     | `"Hello 123".match(/\d+/)` → `["123"]`                | 使用正则表达式匹配字符串               |
| `search(regexp)`                    | `"Hello World".search(/World/)` → `6`                 | 搜索匹配正则表达式的第一个索引位置     |
| `localeCompare(str)`                | `"apple".localeCompare("banana")` → `-1`              | 根据区域设置比较两个字符串的排序关系   |

# 10 数组

数组中的元素可以是不同的数据类型的

```javascript
const number = new Array(1,2,3,4);

console.log(number)
```

访问数组中的元素，索引是从0开始的

```javascript
const number = new Array(1,2,3,4);

console.log(number[0])

number[1] = 5
```

const类型的数组内部元素可以被改变，但是其整体不能直接全部被赋一个新值

- 数组末尾添加元素：`number.push(5)`
- 数组头部添加元素：`number.unshift(0)`
- 删除数组末尾元素：`fruits.pop()`
- 检验变量是否是一个数组：`Array.isArray("hello")`
- 找寻元素索引：`number.indexOf("oranges")`

# 11 对象

表示为键值对

数组和对象都可以作为对象的属性

```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  hobbies: ["music", "movies", "sports"],
  address: {
    street: "50 main st",
    city: "Boston",
    state: "MA",
  },
};

console.log(person.firstName);
```

通过`.`来访问对象的属性

找数组里的元素就用[]

找对象的对象里的元素就连续`.` 

## 对象解构赋值





```javascript
const person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  hobbies: ["music", "movies", "sports"],
  address: {
    street: "50 main st",
    city: "Boston",
    state: "MA",
  },
};

const {
  firstName,
  lastName,
  address: { city },
} = person;

console.log(firstName, city)
```

打印出来的结果就是`John Boston`

## 添加新的属性

`person.email = "john@gmail.com"`

这样就给这个对象添加了新的属性



# 12 对象数组和json

```javascript
const todos = [
  {
    id: 1,
    text: "Take out trash",
    isCompleted: true,
  },
  {
    id: 2,
    text: "Meeting with boss",
    isCompleted: true,
  },
  {
    id: 3,
    text: "Dentist appt",
    isCompleted: false,
  },
];
console.log(todos);
console.log(todos[1].text);
```

转换成Json格式

```javascript
const todoJSON = JSON. stringify(todos);
console.log(todoJSON);
```

就会输出json格式的结果

# 13 If条件判断

== 表示值相同，类型可以不同， ===表示值和类型都相同

或||

且&&

# 14 三目运算符



# 15 switch条件语句





# 16 for while循环语句













