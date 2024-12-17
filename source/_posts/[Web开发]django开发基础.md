---
title: django开发基础
date: 2024-12-17 13:07:46
categories: Web开发
cover: /img/cover12.jpg
tags: 
  - 后端
  - python
description: "Pyhonweb开发django学习笔记"
---



# Django

[toc]



# 一、初步了解Django

## 1.1 创建项目

- 命令行
- Pycharm创建项目
  - 在标准的基础上默认给我们增加了点东西
  - 创建了一个templates目录（删除）
  - setting文件中，选中的部分要删除掉![](https://pic.imgdb.cn/item/63c2cba9be43e0d30edb73fa.png)

## 1.2 文件介绍

```shell
web
├── manage.py			# 项目的管理,包括: 启动项目,创建app, 数据管理【不要动】【很重要】
└── web
    ├── asgi.py			# 接收网络请求【不要动】
    ├── __init__.py
    ├── settings.py		# 项目配置(模板配置,数据库配置,注册app)【常常操作】
    ├── urls.py			# url和函数的对应关系，路径【常常操作】
    └── wsgi.py			# 接收网络请求【不要动】
```



## 1.3 APP的创建和说明

### 添加新的app

终端在当前项目目录下，输入"python manage.py startapp app名字"

查看app下的文件

```bash
app01/
├── admin.py [固定，不用动]
├── apps.py [固定，不用动]
├── __init__.py
├── migrations [固定，不用动]
│   └── __init__.py
├── models.py [重要]对数据库进行操作
├── tests.py [固定，不用动]
└── views.py [重要] 在urls里调用的函数指向这里的视图函数

```

应用【blog】中各个目录作用：

- **migrations:** 用于记录models中数据的变更。
- **admin.py:** 映射models中的数据到Django自带的admin后台。
- **apps.py:** 在新的Django版本中新增，用于应用程序的配置。
- **models.py:** 创建应用程序数据表模型（对应数据库的相关操作)。
- **test.py:** 创建Django测试。
- **views.py:** 控制向前端显示那些数据

### 注册app

打开app下的apps.py文件，找到里面的类

![](https://pic.imgdb.cn/item/63c383edbe43e0d30e0ab9a7.jpg)

添加到setting文件的这里

![](https://pic.imgdb.cn/item/63c3842fbe43e0d30e0b1aa5.jpg)



### 创建页面

编辑`views.py`里的 视图函数

```python
from django.shortcuts import render,HttpResponse
def index(request):
    return HttpResponse('welcome to Django blog!')
```

编辑的`urls.py` 来指定访问路由

前面放访问路径，后面放函数[建立路径与函数的映射关系，以后访问路径就会执行这个函数]

记得import view文件

```python
from django.urls import path
from app01 import views
urlpatterns = [
    # path("admin/", admin.site.urls),
    path("index/", views.index)
]
```

- 命令行启动Django或者pycharm里直接运行

浏览器访问
![](https://pic.imgdb.cn/item/63c3860abe43e0d30e0e2d11.jpg)

> 再来一个

编辑`views.py` 视图函数

```python
from django.shortcuts import render,HttpResponse
def index(request):
    return HttpResponse('welcome to Django blog!')

def user_list(request):
    return HttpResponse("用户列表")

```

编辑`urls.py` 来指定访问路由

```python
from django.contrib import admin
from django.urls import path
from app01 import views
urlpatterns = [
    # path("admin/", admin.site.urls),
    path("index/", views.index),
    path("user_list/", views.user_list),
]

```

- 访问浏览器![](https://pic.imgdb.cn/item/63c386abbe43e0d30e0f4eb7.jpg)

> 总结：就是先在url里创建映射关系，然后去views里写视图函数

## 1.4 templates模板

> 为了使用HTML,这里开始引入templates模板

**注意:** 可以在app下创建`templates`目录,也可以在主目录下创建`templates`目录

- 1.优先去项目的根目录下寻找
- 2.根据app的注册顺序去app的目录下templates下寻找

- 所以我们把刚开始配置的根目录下的templates文件夹删掉了



### templates语法

>  如果说我们从数据库中取到了数据,如何在`html`页面中进行展示呢,这里需要用到templates的基本语法

#### 单一变量

- 首先配置路由

<img src="https://pic.imgdb.cn/item/63c3899dbe43e0d30e15b4c3.jpg" style="zoom:50%;" />

- 然后写视图函数
  - 可以看到参数分别是request、模版名字、文本（）

![](https://pic.imgdb.cn/item/63c38973be43e0d30e15665e.jpg)

- 然后在html中可以调用到传过来的值
  - tpl.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>  模版语法的学习 </h1>
<h1> {{ n1 }} </h1>
</body>
</html>
```

- 访问

<img src="https://pic.imgdb.cn/item/63c38a57be43e0d30e171d4b.jpg" style="zoom:33%;" />

> 单一变量就直接用花括号，意思是传进去是什么样就显示成什么样

#### 列表

- 修改视图函数

```python
def tpl(request):
    name = "丸子"
    roles = ["管理员","CEO","保安"]
    return render(request, "tpl.html", {"n1":name,"n2":roles})
```

- 在html中需要这样取

```html
<div> {{ n2.0}} </div>
<div> {{ n2.1}} </div>
<div> {{ n2.2}} </div>
```

- 效果

<img src="https://pic.imgdb.cn/item/63c38b90be43e0d30e1a1036.jpg" style="zoom:33%;" />

#### 循环【列表】

> 里面元素太多了，一个一个索引显然不方便，就可以用循环，有点像java里的el表达式

```html
<div>
    列表循环:
    {% for item in n2 %}
        <span>{{ item }}</span>
    {% endfor %}
</div>
```

- 效果

<img src="https://pic.imgdb.cn/item/63c38c2ebe43e0d30e1b853d.jpg" style="zoom:33%;" />

#### 字典

修改`views.py`

```python
def tpl(request):
    name = "丸子"
    roles = ["管理员","CEO","保安"]
    user_info = {"name": "张三", "age": 25, "sex": "男"}
    return render(request, "tpl.html", {"n1":name,"n2":roles,"n3":user_info})
```

修改`tpl.html`，根据键取获取值

```html
<div>
    {{ n3 }}<br>
    {{ n3.name }}
    {{ n3.age }}
    {{ n3.sex }}
</div>
```

- 效果

![](https://pic.imgdb.cn/item/63c38d4dbe43e0d30e1ddd02.jpg)

#### 循环【字典】

> 获取值 `values`

```django
<div>
    {% for v in n3.values %}
        <li>{{ v }}</li>
    {% endfor %}
</div>
```

> 获取键 `keys`

```django
    <div>
        {% for k in n3.keys %}
            <li>{{ k }}</li>
        {% endfor %}
    </div>
```

> 获取键和值 `items`

```django
<div>
    {% for k,v in n3.items %}
        <li>{{ k }} = {{ v }}</li>
    {% endfor %}
</div>
```

- 效果

<img src="/Users/xuan/Library/Application Support/typora-user-images/image-20230115132508690.png" alt="image-20230115132508690" style="zoom:25%;" />

#### 列表套字典

修改视图函数

```python
def tpl(request):
    name = "丸子"
    roles = ["管理员","CEO","保安"]
    user_info = {"name": "张三", "age": 25, "sex": "男"}
    user_list = [
        {"name": "张三", "age": 25, "sex": "男"},
        {"name": "李四", "age": 18, "sex": "男"},
        {"name": "王五", "age": 22, "sex": "女"},
    ]
    return render(request, "tpl.html", {"n1":name,"n2":roles,"n3":user_info,"n4":user_list})
```

修改html

```django
<div>
    {% for item in n4 %}
        <div>{{ item.name }} {{ item.age }} {{ item.sex }}</div>
    {% endfor %}
</div>
```

- 效果

<img src="https://pic.imgdb.cn/item/63c38f15be43e0d30e21050f.jpg" style="zoom:33%;" />

#### 条件判断

```django
{%  if n1 == "poker" %}
    <h3>嘿嘿嘿</h3>
{% elif n1 == "toker" %}
    <h3>哈哈哈</h3>
{% else %}
    <h3>呵呵呵</h3>
{% endif %}
```

### templates小结

本质上：模版语法是在HTML中写一些占位符，由数据对这些占位符进行替换和处理

![](https://pic.imgdb.cn/item/63c39047be43e0d30e235ca4.jpg)

## 1.5 请求和响应

**重定向:** 浏览器向某个网站发送请求,网站返回给浏览器一个新的URL,浏览器去访问这个新的URL地址

```python
def something(request):
  # request是一个对象，封装了用户发送过来的所有请求相关的数据
  # 1. [请求]获取请求方式 GET/POST
  print(request.method)
  # 2. [请求]在URL上传递值
  print(request.GET)
  # 3. [请求]在请求体中提交数据
  print(request.POST)
  # 4. [响应] HttpResponse("返回内容")，内容字符串内容返回给请求者
  # return HttpResponse("返回内容")
  # 5. [响应] 读取HTML的内容+渲染（替换）->字符串，返回给用户浏览器
  return render(request,"something.html",{"title":"来了"})
	# 6. [响应] 让浏览器重定向到其他的页面
  return redirect("https://www.baidu.com")
```

- 前面讲的都是第一种方式
- 浏览器按第二种方式处理重定向，什么意思呢，就是说浏览器向服务器发送请求时，服务器返回了一个url（而不是经过渲染的html），让浏览器自己去访问

![](https://pic.imgdb.cn/item/63c3b9aebe43e0d30e76c9f5.jpg)

### 案例：用户管理

修改`views.py`,新增`login`函数

```python
def login(request):
    if request.method == "GET":
        return render(request, "login.html")

    # 如果是 POST 请求,获取用户提交的数据
    print(request.POST)
    username = request.POST.get("user")
    password = request.POST.get("password")
    if username == "poker" and password == "123":
        return HttpResponse("登录成功") 

    #return HttpResponse("登录失败")
    return render(request, "login.html", {"error_msg": "用户名或密码错误"})
```

url里增加`login`

```python
path('login/', views.login),
```

在`templates`下新建`login.html`

```django
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <h1>用户登录</h1>
    <form method="post" action="/login/">

        {% csrf_token %}

        <input type="text" name="user", placeholder="用户名">
        <input type="password" name="password", placeholder="密码">
        <input type="submit" value="提交">
        <span style="color: red;">{{ error_msg }}</span>
    </form>
</body>
</html>

```



- 出现这种错误要在form表单中加上`{% csrf_token %}`，用来校验是不是我这个网页发过来的请求<img src="https://pic.imgdb.cn/item/63c3c501be43e0d30e8d2ec4.jpg" style="zoom:33%;" />

# 二、数据库操作

Django开发数据库更简单，内部提供了ORM框架

![](https://pic.imgdb.cn/item/63c3e817be43e0d30ecbafff.jpg)

## 2.1 ORM

ORM可以帮助我们做两件事:

- 创建/修改/删除数据库中的表(无法创建数据库)
- 操作表中的数据
- 都不用写sql语句，orm会将其翻译成sql

## 2.2 Django连接数据库

首先在数据库里创建一个database

```sql
create database mydb DEFAULT CHARSET utf8 COLLATE utf8_general_ci;
```

然后在settings.py进行配置和修改

```python
DATABASES = {
    'default':{  		  	   
      'ENGINE':'django.db.backends.mysql', 
        'NAME':'mydb',
        'USER':'root',
        'PASSWORD':'Syz123!@#',
        'HOST':'127.0.0.1',
        'PORT':'3306',
    }
}

```

## 2.3 Django操作表

- 创建表
- 删除表
- 修改表

配置app01下的`models.py`

> 会根据自定义的类创建跟app同名的表

```python
from django.db import models

# Create your models here.
class UserInfo(models.Model):
    name = models.CharField(max_length=20)
    password = models.CharField(max_length=20)
    age = models.IntegerField()

```

- orm会自动将上述语句变为sql并执行

```sql
create table app01_userInfo(
    id bigint auto_increment primary key,
    name varchar(20),
    password varchar(20),
    age int
)
```

- 执行需要在根目录的终端下输入两步指令

> python3 manage.py makemigrations
> python3 manage.py migrate

- 然后就可以看到数据库中有很多表（有我们自己创的userinfo，还有其他django默认配置的）
- <img src="https://pic.imgdb.cn/item/63c41ee9be43e0d30e3ebcc7.jpg" style="zoom:33%;" />
