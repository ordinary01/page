---
title: docker修改镜像名称
date: 2020-06-27 19:21:15
tags:
    - docker
categories:
    - docker
---

``` bash
[root@localhost ~]# docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
pujh/centos         tomcat-centos       70ff7873d7cd        About an hour ago   612 MB
docker.io/centos    latest              9f38484d220f        11 days ago         202 MB
[root@localhost ~]# docker tag 70ff7873d7cd my_centos:tomcat-centos
```