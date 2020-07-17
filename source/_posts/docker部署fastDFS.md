---
title: docker部署fastDFS
date: 2020-07-16 16:36:47
tags:
  - fastDFS
  - docker
categories:
  - docker
---

docker环境部署FastDFS文件系统
查找 fastdfs镜像   docker search fastdfs

<!-- more -->
1. 拉取镜像

    ```bash
    docker pull delron/fastdfs
    ```

2. 启动tracker服务

   ```bash
    docker run -d --network=host --name tracker -v /home/tracker:/var/fdfs delron/fastdfs tracker
    ```

3. 启动storage服务

    ```bash
    docker run -d --network=host --name storage -e TRACKER_SERVER=你的ip:22122 -v /home/storage:/var/fdfs -e GROUP_NAME=group1 delron/fastdfs storage
    ```

4. 查看已经启动的容器

    ```bash
    docker ps
    ```

    ![查看启动docker](img/查看启动docker.png)

注：
fastdfs默认的端口有三个8888,23000,22122），8888是默认的nginx代理端口，23000是storage服务端口，22122是tracker服务端口，运行时需要将这三个端口对外开放

```bash
firewall-cmd --zone=public  --permanent --add-port=23000/tcp

firewall-cmd --zone=public  --permanent --add-port=22122/tcp

firewall-cmd --zone=public  --permanent --add-port=8888/tcp

```
