---
title: spring-boot-jpa使用IDEA生成实体类
date: 2019-03-10 23:35:37
tags:
  - IDEA
categories:
  - spring-boot问题
---

1. View->Tool Windows->DataBase 添加数据库<!-- more -->

2. File->Project Structure 如果没有点击加号加上 model ![Project Structure图片](img/Project Structure图片.png)
3. 添加完成后就会出现 Persistence 窗口(只有执行第二步之后才会出现)![Persistence位置.png](img/Persistence位置.png)
4. 在 Persistence 窗口 右键选择->Generate Persistence Mapping->选择 By Database Schemas![Database Schemas](img/Database Schemas.png)
5. 选择第 4 步的 By Database Schema 之后就会出现下面的样式选择相应的数据库表、设置表中字段与实体类的对应关系类型、以及生成的实体类所在包的位置，点击确定后就会在相应的位置生成文件![选择数据文件](img/选择数据文件.png)
