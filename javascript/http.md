---
title: http理解
---



HTTP是什么，概念：

**超文本传输协议**（[英文](https://zh.wikipedia.org/wiki/%E8%8B%B1%E6%96%87)：**HyperText Transfer Protocol**，[缩写](https://zh.wikipedia.org/wiki/%E7%B8%AE%E5%AF%AB)：**HTTP**）是一种用于分布式、协作式和[超媒体](https://zh.wikipedia.org/w/index.php?title=%E8%B6%85%E5%AA%92%E9%AB%94&action=edit&redlink=1)信息系统的[应用层协议](https://zh.wikipedia.org/wiki/%E5%BA%94%E7%94%A8%E5%B1%82)[[1\]](https://zh.wikipedia.org/wiki/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%8D%8F%E8%AE%AE#cite_note-ietf2616-1)。HTTP是[万维网](https://zh.wikipedia.org/wiki/%E5%85%A8%E7%90%83%E8%B3%87%E8%A8%8A%E7%B6%B2)的数据通信的基础。

http协议：服务端和客服端数据传输的工具

HTTP 是基于 TCP/IP 协议的[**应用层协议**](http://www.ruanyifeng.com/blog/2012/05/internet_protocol_suite_part_i.html)。它不涉及数据包（packet）传输，主要规定了客户端和服务器之间的通信格式，默认使用80端口。

- 最早版本是1991年发布的0.9版。该版本极其简单，只有一个命令`GET`。

  ​


### 参考链接：

[http，请求头、相应头介绍](https://www.jianshu.com/p/b5993a20292a)

[content-type理解](https://segmentfault.com/a/1190000003002851)

#### 问题记录：

1. 对于content-type的理解，如果客户端请求时设置的ct于服务端定义的不同，会出现什么情况；

2. ```
   Failed to load https://wx.dashixiongky.com/api/v1/0/province: Request header field Access-Control-Allow-Headers is not allowed by Access-Control-Allow-Headers in preflight response.
   ```

   问题描述：

   > 前端代码通过nginx配置在服务器A上；后台服务也运行在A上；
   >
   > 后台接口用于微信小程序，所以使用https协议；https://wx.dashixiongky.com/
   >
   > 前端页面访问地址：http://47.94.251.1:8088/
   >
   > 根据同源跨域策略，一个http、一个https；其实已经出现跨域了。
   >
   > **但是在这中情况下，发送GET请求成功；发送POST请求返回200，但是报错；**
   >
   > **最终解决方案：** 后台服务设置跨域解决；

   **思考：** 是不是真的跨域了？ 为什么跨域了还能发送get请求；发送post请求返回200状态码？

   **学习：** **CORS**（跨域资源共享 - Cross-origin resource sharing）的实现原理；



## CORS

[参考链接-阮一峰](http://www.ruanyifeng.com/blog/2016/04/cors.html)

#### 简单请求：

请求方式：只能是`HEAD, GET, POST`中的一种

Content-Type：只限于三个值`application/x-www-form-urlencoded`、`multipart/form-data`、`text/plain`

只会发送一次请求；

**如果是登录验证需要带cookie时：**

服务端需要设置：**Access-Control-Allow-Credentials： true**



