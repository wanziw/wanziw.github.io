---
title: 'Hexo博客在多个设备同步'
date: 2024-11-28 19:08:08
categories: Hexo教程
cover: /img/cover4.jpg
description: '实现Hexo博客在不同的设备上都可以使用和上传'
---

博客链接1 ：[Hexo搭建博客的多终端同步问题](https://zhuanlan.zhihu.com/p/476603074)

博客链接2:[Hexo博客多台电脑设备同步管理](https://www.jianshu.com/p/0558c041e56d)

今天想把个人博客网站同时在macbook和mac mini上进行共同协作使用。其实最好的就是直接把项目放在icloud上面，就不用折腾这么多了，但是想探寻一下原理就搞了一下午。

原理其实很简单，只要两边能实现更新github上的部署文件就好了。新创建一个分支用来存源文件。

1. 对于同时使用一个github项目,前面写的博客已经写了解决办法了，就是SSH keys
2. 还有一个问题就是另一边疯狂报错，把这些报错的包一个个卸载了重新装，然后没装的包装一下

如果你已经在一台电脑上完成了博客的搭建，那么你是否想过如何在其它电脑上同步博客呢~

> 其实原理很简单，`hexo g`将我们的源文件部署， `hexo d`上传的只是网页部署文件，这些文件上传到了 github的 `master`分支，我们在另一台电脑上如果能够拥有源文件的话，同样将这些部署文件上传到 github 的 `master`分支即可，那么其实我们要做的就是备份源文件。
>
> 那么我们可以在github的blog仓库**新建一个分支，存储源文件，亦或者新建一个仓库，存储源文件**即可，这样我们就可以在多个终端间同步源文件，而后就可以进行博客文件的终端同步了。

# Github 操作

github Blog仓库中**新建一个分支 hexo**

- 参考博客1

# 初始电脑本地操作

本地任意一空白目录下 git clone 之前的代码

```bash
git clone git@github.com:<your rep url ,eg :name.github.io.git>
```

clone成功后，删除掉除去`.git`之外的所有文件夹

把之前的博客源文件复制过来，除去 `.deploy_git`

新建or修改 `.gitignore`文件

```text
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

如果你在`themes`文件夹下 clone 过其它主题文件，把其中的 `.git`文件夹删除掉

先切换hexo分支



上传文件到hexo分支

```text
git add .
git commit -m "backup blog source file0305"
git push 
```

如果没有报错，此时github端应该就可以看到备份的源文件了。

# 另一台终端操作

首先进行一些基础配置，安装git nodejs 配置git连接Github

```text
npm install hexo-cli -g			# intall hexo

# 在该电脑的本地文件夹下clone Blog源文件
git clone <url>
```

clone 成功后，进入blog文件夹下，安装之前安装的插件

```text
npm install
npm install hexo-deployer-git --save
npm install hexo-hexo-renderer-marked #图片
```

然后就可以在新电脑上写博客了，将博客部署到网站后，记得备份源文件
```aiignore
hexo g
hexo d
```

```text
git add .
git commit -m ""
git push 

## 多台终端写blog ，记得先和github端 同步 ##
git pull
```



# 疯狂报错

**出了什么错就重新下载这个包** 配合chatgpt



