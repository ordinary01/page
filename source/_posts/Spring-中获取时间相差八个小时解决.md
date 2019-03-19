---
title: Spring 中获取时间相差八个小时解决
date: 2019-03-10 23:43:31
tags:
  - spring-boot
categories:
  - spring-boot问题
---

# 获取时间与真实时间相差八小时问题

## 问题 1：

spring 时间**格式化转换**之后与当前时间相差八个小时

<!-- more -->

### 原因：

spring 默认使用 jackson 转换日期， jackson 默认时区与北京时间相差八个小时

### 解决方式

在项目的配置文件 _application.properties_ 加上下面配置

```bash
spring.jackson.time-zone=GMT+8
```

==============================================

## 问题 2：

数据库获取时间与当前时间相差八个小时（使用的持久层框架为 spring-boot-jpa ）

### 原因 2：

数据库获取的时间与北京时区存在差异

### 解决方式 2

```bash
spring.datasource.url=jdbc:mysql://IP:3306/database?useUnicode=true&characterEncoding=utf-8&serverTimezone=GMT%2b8
```

_注：
建议将两种方式都应用到项目中，以防万一_
