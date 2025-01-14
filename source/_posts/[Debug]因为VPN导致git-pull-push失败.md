---
title: 因为VPN导致git pull/push失败
date: 2025-01-14 12:28:44
categories: bug解决日记
description: "解决Git连接失败：Failed to connect to github.com port 443 after 21090 ms: Couldn‘t connect to server ‍"
tags: github
---

# 问题定位
首先，确认你是否在使用VPN。
VPN的使用可能会改变本机的系统端口号，从而影响到Git的正常连接。

```bash
$ git pull origin main
fatal: unable to access 'https://github.com/MapleRainGy/first-repo.git/'
:Failed to connect to github.com port 443 after 21111 ms: Could not connect to server
```


 # 1.设置端口号

```bash
git config --global http.proxy 127.0.0.1:7890
git config --global https.proxy 127.0.0.1:7890
```

# 2.查看是否设置成功

```bash
git config --global -l
```

# 3.刷新DNS缓存

```bash
ipconfig
```

# 4.重新push：

```bash
$ git pull origin main
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 942 bytes | 188.00 KiB/s, done.
...
```

# 5. 总结

| 问题场景    | 解决方法        | 重要命令                                                     |
| :---------- | :-------------- | :----------------------------------------------------------- |
| 使用VPN时   | 调整Git代理设置 | git config --global http.proxy, git config --global https.proxy |
| 未使用VPN时 | 取消Git代理设置 | git config --global --unset http.proxy, git config --global --unset https.proxy |

参考链接：[解决Git连接失败：Failed to connect to github.com port 443 after 21090 ms: Couldn‘t connect to server ‍](https://cloud.tencent.com/developer/article/2405656)

