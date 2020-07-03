---
title: node使用sharp修改图片中间原型头像
date: 2020-07-03 15:07:55
tags:
  - node
categories:
  - node学习
---

需要将网络上的图片，中间的头像更改为新图片，并且返回生成图片的文件流
<!-- more -->
```node

const sharp = require('sharp');
const fs = require("fs");
const UUID = require('node-uuid');
const got = require("got");

//fileBuffer图片的buffer，uriPath网络图片
//先使用got下载网络图片，然后使用sharp合成
  async baseImgOperations(fileBuffer, uriPath) {
    const sharpStream = sharp({
      failOnError: false
    });
    const promises = [];
    var uuid = UUID.v1();
    //http://www.iocoder.cn/images/common/wechat_mp_2017_07_31_bak.jpg
    got.stream(uriPath).pipe(sharpStream);
    //got.stream(uriPath).pipe(sharpStream);
    var fileName = uuid + ".png";
    const roundedCorners = Buffer.from(
      '<svg><circle r="60" cx="60" cy="60"/></svg>'
    );

    const baseImgFile= await sharpStream.clone().resize(200, 200);
    await baseImgFile.composite([{
      input: roundedCorners,
      blend: 'dest-in'
    }]).png().toFile(fileName);

    const resultBuff= await
      sharp(fileBuffer).resize({
        width: 280,
        height: 280
      }).composite([{
        input: fileName
      }])
        .sharpen()
        .withMetadata()
        // .webp({
        //   quality: 90
        // })
        .png()
        .toBuffer().then(info => {
        fs.unlinkSync(fileName);
        return info;
      });

    console.log(resultBuff);

    return resultBuff;

  }


```
