---
title: springboot 连接数据库报错（useSSl）
date: 2019-03-10 23:50:16
tags:
    - springboot data
categories:
    - spring-boot
---

```bash
WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
```

由于使用 ssl 连接，但是没配置 ssl 信息；如果不用 ssl 连接可以在连接中增加

```bash
jdbc.url=jdbc:mysql://localhost:3306/esps?useSSL=false
```
