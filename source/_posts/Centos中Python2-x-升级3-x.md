---
title: Centos中Python2.x 升级3.x
date: 2019-03-11 00:12:29
tags:
  - centos
  - python
categories:
  - 环境问题
---

- 查看当前 python 版本

```bash
python --version
python -V
```
<!-- more -->
- 下载最新的 python 版本

```bash
wget https://www.python.org/ftp/python/3.5.2/Python-3.x.x.tgz
```

- 解压

```bash
tar -zxvf Python-3.7.2.tgz
```

- 进入解压的 python 文件夹

```bash
cd Python-3.5.2/
 ./configure
```

- 可能会报错

```bash
configure: error: no acceptable C compiler found in $PATH
```

- 报错是由于 linux 没有合适的编译器，安装编译器即可( yum 如果有问题可以参考 [yum 更新](/2019/03/10/最小化-Centos7-安装没有-ifconfig命令，以及更新-yum/) )

```bash
yum install make gcc gcc-c++
```

- 然后再执行

```bash
 ./configure
```

- 编译(时间较长)

```bash
make
```

- 安装

```bash
make  install
```

- 这个时候查看 python 版本的还是 2.x 访问 python3 的版本是 3.x; 查看 python 的链接情况

```bash
 ls -al /usr/bin | grep python
-rwxr-xr-x.  1 root root      11216 12月  1 2015 abrt-action-analyze-python
lrwxrwxrwx.  1 root root          7 8月  30 12:11 python -> python2
lrwxrwxrwx.  1 root root          9 8月  30 12:11 python2 -> python2.7
-rwxr-xr-x.  1 root root       7136 11月 20 2015 python2.7
```

- 将原来的 python 的软链接重命名

```bash
  mv /usr/bin/python /usr/bin/python.bak
```

- 将 python 链接至 python3

```bash
 ln -s /usr/local/bin/python3 /usr/bin/python
```

变为
![f6a97143f25a4971157854be5a0e310.png](img/f6a97143f25a4971157854be5a0e310.png)

- 查看 python 发现已经是 3.x 的版本

最后会发现 yum 不能使用，由于 yum 引用了 python 需要将 yum 的配置更改

```bash
 vi /usr/bin/yum
 vi /usr/libexec/urlgrabber-ext-down
```

将 _#!/usr/bin/python 改为 #!/usr/bin/python2.7_ 就好了

本文参考：
<https://blog.csdn.net/liang19890820/article/details/51079633>
