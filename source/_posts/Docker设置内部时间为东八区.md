---
title: Docker设置内部时间为东八区
date: 2019-03-10 23:24:27
tags:
    - docker
categories:
    - docker
---
在 Dockerfile 或者 Docker Compose 中加入

``` bash
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' >/etc/timezone
```
