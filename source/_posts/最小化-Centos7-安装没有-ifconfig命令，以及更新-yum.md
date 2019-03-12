---
title: 最小化 Centos7 安装没有 ifconfig命令，以及更新 yum
date: 2019-03-10 23:02:48
tags:
  - centos
categories:
  - 环境问题
---

安装 net 工具

```bash
yum install net-tools
```

安装过程中可能会报 yum 异常，可以更改 yum 源
可以参考 163 的源网站 <http://mirrors.163.com/.help/centos.html>

1.备份

```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

2.下载相应镜像到指定目录中

```bash
cd /etc/yum.repos.d/
wget http://mirrors.163.com/.help/CentOS7-Base-163.repo
```

3.生成缓存

```bash
yum clean all
yum makecache
```
