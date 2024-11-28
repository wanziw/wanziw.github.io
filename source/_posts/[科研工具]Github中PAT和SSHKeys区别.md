---
title: Github中PAT和SSHKeys区别
date: 2024-11-28 18:02:27
categories: 科研工具
description: "今天研究两台设备共同运行Github项目的问题，关于一般项目配置个人访问令牌和SSHkeys的问题"
tags: Github使用
cover: /img/cover5.jpg
---


> 自己使用github一直没搞懂这些公钥、秘钥啥的，今天搞懂了一点就记录一下


#  PAT和SSH keys区别

> 在GitHub中，token和SSH keys都是用于身份验证和安全访问仓库的方法。Token是一种 访问令牌，可以代替密码进行身份验证。
>
> GitHub允许创建具有不同权限级别的个人访问令牌（Personal Access Token, PAT），用于命令行操作、第三方应用等。
>
> SSH keys是一种加密方法，用于在两个通信方之间建立一个安全的连接。GitHub允许创建SSH keys，用于将本地git客户端与GitHub仓库安全关联。



**如果 URL 以 `https://` 开头**，则使用的是 **HTTPS** 协议，通常需要使用 **Personal Access Tokens (PATs)** 进行身份验证。

**如果 URL 以 `git@github.com:` 开头**，则使用的是 **SSH** 协议，依赖于 **SSH 公钥** 进行身份验证。

- SSH
  - 用于通过 SSH 协议进行 Git 操作（如 `git push`、`git pull`）和与 GitHub 进行安全通信。
  - 基于公钥加密，使用密钥对（公钥和私钥）进行身份验证
  - 保存在本地，适合长期使用，**在每台设备上生成和管理密钥对**
  - 每次要输入密码
- PAT
  - 通过 HTTPS 协议进行 Git 操作，或通过 GitHub API 进行身份验证
  - 类似于**密码**，没有加密，但是就只能看一次，而且有**过期时间**，需要重新设置
  - 可以**细化权限**
  - 可以不用输入密码，详见以前写的改bug的博客里





#  SSH keys 同一个Github账号关联多个设备

我的需求是：两个设备上面运行同一个项目

SSH keys是跟账户相关，Deploy keys是某个项目下面的settings中添加的，只跟这个项目有关

- [【Git/SVN】 SSH keys和Deploy key区别](https://blog.csdn.net/Umbrella_Um/article/details/97324018)
  - github账户的SSH keys，相当于这个账号的最高级key，只要是这个账号有的权限（任何项目），都能进行操作。
  - 仓库的Deploy keys，顾名思义就是这个仓库的专有key，用这个key，只能操作这个项目，其他项目都没有权限。
    -  Deploy Keys不适合多人开发的项目，反正我也没用过

## SSH 公钥

- **用途**：用于通过 SSH 协议进行 Git 操作（如 `git push`、`git pull`）以及访问 GitHub API。

- **安全性**：通过公钥加密认证，提供高度安全的连接。

  

- **配置**：需要在每台设备上生成一对密钥（私钥和公钥），然后将公钥添加到 GitHub 账户中。

- **适用场景**：适用于需要频繁进行 Git 操作的开发者，特别是在本地开发环境中。

## 流程

```bash
ls ~/.ssh
```

如果你看到类似 `id_rsa` 和 `id_rsa.pub` 的文件，说明已有 SSH 密钥。可以跳过生成新密钥的步骤，直接使用现有密钥。

### 1生成密钥

使用SSH自带的密钥生成工具，如ssh-keygen生成公钥

xxx@qq.com替换为自己的邮箱

```
ssh-keygen -t rsa -C xxx@qq.com
```

这样就生成了密钥一般存储在（`/Users/你的用户名/.ssh/id_rsa`）这样的路径下面

### 2 复制公钥

**复制公钥内容**：

在终端中运行以下命令将公钥内容复制到剪贴板：

```bash
pbcopy < ~/.ssh/id_rsa.pub
```

如果 `pbcopy` 不可用，可以手动复制：

```bash
cat ~/.ssh/id_rsa.pub
```

然后选择并复制输出的完整内容。



### 3 github上面添加公钥

**导航到 SSH 和 GPG 密钥设置**：

- 点击右上角的头像，选择 **Settings（设置）**。
- 在左侧菜单中，点击 **SSH and GPG keys**。

**添加新的 SSH 密钥**：

- 点击 **New SSH key** 按钮。
- **Title**：输入一个描述性名称，如“ MacBook SSH 密钥”。
- **Key**：粘贴你复制的公钥内容。
- 点击 **Add SSH key**。



### 4 新设备可能需要配置账号以及输入密码

```bash
git config --global user.email "注册用的邮箱"
git config --global user.name "用户名"
```

### 5 进行仓库的push和pull

[**如何使用git（同一账号）在多台电脑协同做工**](https://www.cnblogs.com/Ye-zixiao/p/12233193.html)





别的可能的报错[「详细教程」使用git将本地项目上传至Github仓库（MacOS为例）](https://blog.csdn.net/qq_36332660/article/details/131024361)





# 配置个人访问令牌（PATs）

我之前的需求是Hexo项目可以进行上传，我也不知道为啥配置了PATs，尝试一下能不能

- **Repository access** 部分，选择 **Only select repositories** 并指定目标仓库

今天我才知道，我是两个都配置了，在hexo项目_config.yml项目修改项目url
如果是ssh的就每次输入私钥密码
如果是http的就在每次有令牌，不用自己输入密码，但是定期会过期
```
deploy:
    type: git
    repository: git@github.com:xxx/xxx.github.io.git
    branch: mater
```


需要定期更新

[【Debug】hexo-github 令牌认证](https://wanziw.club/2024/07/19/%5BDebug%5Dhexo-github%E4%BB%A4%E7%89%8C%E8%AE%A4%E8%AF%81/)

[[GitHub使用Personal access token ](https://www.cnblogs.com/chenyablog/p/15397548.html)](https://www.cnblogs.com/chenyablog/p/15397548.html)



# 对于一些使用场景

1. **多人协作的项目**

   1. SSH+Github
   2. 每个开发者使用自己的 SSH 密钥，自己进行Github仓库和本地代码之间的的配置
   3. 项目管理者可以在**设置仓库权限**：
      - 确保每个开发者在仓库中拥有适当的权限（如 `Read`、`Write`、`Admin`）。
      - 可以通过 **Teams** 和 **Collaborators** 管理权限。

2. **同一个账户多个设备之间**

   1. 为每台设备生成独立的 SSH 密钥，并将所有公钥添加到 GitHub 账户中。
   2. 每台设备有独立的密钥，单台设备的密钥泄露不会影响其他设备。
   3. 可以在 GitHub 上单独撤销某台设备的密钥，而不影响其他设备。

3. **对于有仓库限制权限的分配**

   1. 推荐使用 SSH Deploy Keys

      1. **每个部署密钥仅限于特定仓库**，减少权限过大的风险。
      2. 可以单独管理每个部署密钥，便于撤销或更新。

   2. 如果 Deploy Keys 不可用，考虑使用 Fine-grained PAT

      1. 可以为**特定仓库和权限**生成 PAT。

         





