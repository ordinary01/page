---
title: nodejs简单页面展示
date: 2020-06-27 22:02:48
tags:
  - node
categories:
  - node学习
---


制作简单的网页服务器
<!-- more -->
```node
const koa=require('koa');
const fs =require('fs');
const mount=require('koa-mount');
const static=require('koa-static');

const app=new koa();

//将静态资源开放，否则相应的静态资源会失效
app.use(
    static(__dirname+'/source/')
)

//设置请求路径为"/" 的操作逻辑
app.use(
    mount('/',async(ctx)=>{
        ctx.body=fs.readFileSync(__dirname+'/source/index.htm','utf-8')
    })
)
//设置端口
app.listen(3000)
```
