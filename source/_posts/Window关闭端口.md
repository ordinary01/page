---
title: Window关闭端口
date: 2019-04-01 11:10:03
tags:
  - window
categories:
  - 环境问题
---
* 查询端口占用进程号

```code
netstat -aon| findstr "8083"
```

<!-- more -->
![查询结果](img/img.png)

* 终止进程

```code
taskkill /F /PID 7264
```