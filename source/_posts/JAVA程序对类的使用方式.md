---
title: JAVA程序对类的使用方式
date: 2019-03-18 23:30:51
tags:
  - jvm
categories:
  - JVM学习
---

java 程序对**类**（`非对象`）的使用方式分为两种：

- 主动使用（类的首次主动使用会导致类的初始化）

<!-- more -->

1. 创建类的实例
2. 访问某个类或者接口的静态变量，或者对该静态变量赋值
3. 调用类的静态方法
4. 反射 Class.forName("com.test.Test");
5. 初始化一个类的子类
6. JVM 启动时被表名为启动类的类
7. JDK1.7 提供的动态语言支持：
   java.lang.invoke.MethodHandle 实例的解析结果 REF_getStatic,REF_putStatic,REF_invokeStatic 句柄对应的类没有初始化则初始化

- 被动使用

所有非主动使用的使用方式都是对类的被动使用，都不会导致类的初始化
