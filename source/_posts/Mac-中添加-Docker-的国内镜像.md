---
title: Mac 中添加 Docker 的国内镜像
date: 2019-03-10 23:52:10
tags:
    - docker
    - MAC
categories:
    - docker
---
1. 点击 Docker 设置

<!-- more -->
![Docker](img/Docker.png)
2. Preferences->Daemon
![添加样式](img/添加样式.png)

**注：**
添加过程中如果出现 No certs for xxx.mirror.aliyuncs.com，可以将 Registry mirrors中的https改为http，然后Apply & Restart就没有这个报错了
 ![no certs error](img/no certs error.png)
