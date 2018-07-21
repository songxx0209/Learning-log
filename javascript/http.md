---
title: http
---



## HTTP是什么，概念：

> HTTP：**超文本传输协议**（Hypertext Transfer Protocol）
>
>  http协议：服务端和客服端数据传输的工具
>
> HTTP 是基于 TCP/IP 协议的[**应用层协议**](http://www.ruanyifeng.com/blog/2012/05/internet_protocol_suite_part_i.html)。它不涉及数据包（packet）传输，主要规定了客户端和服务器之间的通信格式，默认使用80端口。
>
> HTTP协议以明文方式发送内容，不提供任何方式的数据加密，如果攻击者截取了Web浏览器和网站服务器之间的传输报文，就可以直接读懂其中的信息，因此，HTTP协议不适合传输一些敏感信息，比如：信用卡号、密码等支付信息。
>
> HTTPS在http的基础上加入了SSL协议，SSL依靠证书来验证服务器的身份，并为浏览器和服务器之间通信加密。



**HTTP请求方式：**

OPTIONS、GET、HEAD、POST、PUT、DELETE、TRACE、CONNECT



**Request 部分**

| Header              | 解释                                                         | 示例                                                    |
| ------------------- | ------------------------------------------------------------ | ------------------------------------------------------- |
| `Accept`            | 指定客户端能够接收的内容类型                                 | Accept: text/plain, text/html                           |
| Accept-Charset      | 浏览器可以接受的字符编码集。                                 | Accept-Charset: iso-8859-5                              |
| Accept-Encoding     | 指定浏览器可以支持的web服务器返回内容压缩编码类型。          | Accept-Encoding: compress, gzip                         |
| Accept-Language     | 浏览器可接受的语言                                           | Accept-Language: en,zh                                  |
| Accept-Ranges       | 可以请求网页实体的一个或者多个子范围字段<br />扩展：断点续传实现 | Accept-Ranges: bytes                                    |
| Authorization       | HTTP授权的授权证书                                           | Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==       |
| Cache-Control       | 指定请求和响应遵循的缓存机制                                 | Cache-Control: no-cache                                 |
| Connection          | 表示是否需要持久连接。（HTTP 1.1默认进行持久连接）           | Connection: close                                       |
| **Cookie**          | HTTP请求发送时，会把保存在该请求域名下的所有cookie值一起发送给web服务器。<br />浏览器会自动带上**请求域名下的cookie**，用户登录常使用 | Cookie: $Version=1; Skin=new;                           |
| Content-Length      | 请求的内容长度                                               | Content-Length: 348                                     |
| **Content-Type**    | 请求的与实体对应的MIME信息                                   | Content-Type: application/x-www-form-urlencoded         |
| Date                | 请求发送的日期和时间                                         | Date: Tue, 15 Nov 2010 08:12:31 GMT                     |
| Expect              | 请求的特定的服务器行为                                       | Expect: 100-continue                                    |
| From                | 发出请求的用户的Email                                        | From: user@email.com                                    |
| Host                | 指定请求的服务器的域名和端口号                               | Host: www.zcmhi.com                                     |
| If-Match            | 只有请求内容与实体相匹配才有效                               | If-Match: “737060cd8c284d8af7ad3082f209582d”            |
| If-Modified-Since   | 如果请求的部分在指定时间之后被修改则请求成功，未被修改则返回304代码 | If-Modified-Since: Sat, 29 Oct 2010 19:43:31 GMT        |
| If-None-Match       | 如果内容未改变返回304代码，参数为服务器先前发送的Etag，与服务器回应的Etag比较判断是否改变 | If-None-Match: “737060cd8c284d8af7ad3082f209582d”       |
| If-Range            | 如果实体未改变，服务器发送客户端丢失的部分，否则发送整个实体。参数也为Etag | If-Range: “737060cd8c284d8af7ad3082f209582d”            |
| If-Unmodified-Since | 只在实体在指定时间之后未被修改才请求成功                     | If-Unmodified-Since: Sat, 29 Oct 2010 19:43:31 GMT      |
| Max-Forwards        | 限制信息通过代理和网关传送的时间                             | Max-Forwards: 10                                        |
| Pragma              | 用来包含实现特定的指令                                       | Pragma: no-cache                                        |
| Proxy-Authorization | 连接到代理的授权证书                                         | Proxy-Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ== |
| Range               | 只请求实体的一部分，指定范围                                 | Range: bytes=500-999                                    |
| Referer             | 先前网页的地址，当前请求网页紧随其后,即来路                  | Referer: http://www.zcmhi.com/archives/71.html          |
| TE                  | 客户端愿意接受的传输编码，并通知服务器接受接受尾加头信息     | TE: trailers,deflate;q=0.5                              |
| Upgrade             | 向服务器指定某种传输协议以便服务器进行转换（如果支持）       | Upgrade: HTTP/2.0, SHTTP/1.3, IRC/6.9, RTA/x11          |
| User-Agent          | User-Agent的内容包含发出请求的用户信息                       | User-Agent: Mozilla/5.0 (Linux; X11)                    |
| Via                 | 通知中间网关或代理服务器地址，通信协议                       | Via: 1.0 fred, 1.1 nowhere.com (Apache/1.1)             |
| Warning             | 关于消息实体的警告信息                                       | Warn: 199 Miscellaneous warning                         |

**常见头信息介绍：**

Content-type:

1. text/html 

2. text/plain 

3. text/css 

4. text/javascript 

5. application/x-www-form-urlencoded 

   > 是常用的表单发包方式，普通的表单提交，或者js发包，默认都是通过这种方式

6. multipart/form-data 

   > 用在发送文件的post包

7. application/json 

8. application/xml







**Responses 部分**  

| Header             | 解释                                                         | 示例                                                  |
| ------------------ | ------------------------------------------------------------ | ----------------------------------------------------- |
| Accept-Ranges      | 表明服务器是否支持指定范围请求及哪种类型的分段请求           | Accept-Ranges: bytes                                  |
| Age                | 从原始服务器到代理缓存形成的估算时间（以秒计，非负）         | Age: 12                                               |
| Allow              | 对某网络资源的有效的请求行为，不允许则返回405                | Allow: GET, HEAD                                      |
| Cache-Control      | 告诉所有的缓存机制是否可以缓存及哪种类型                     | Cache-Control: no-cache                               |
| Content-Encoding   | web服务器支持的返回内容压缩编码类型。                        | Content-Encoding: gzip                                |
| Content-Language   | 响应体的语言                                                 | Content-Language: en,zh                               |
| Content-Length     | 响应体的长度                                                 | Content-Length: 348                                   |
| Content-Location   | 请求资源可替代的备用的另一地址                               | Content-Location: /index.htm                          |
| Content-MD5        | 返回资源的MD5校验值                                          | Content-MD5: Q2hlY2sgSW50ZWdyaXR5IQ==                 |
| Content-Range      | 在整个返回体中本部分的字节位置                               | Content-Range: bytes 21010-47021/47022                |
| Content-Type       | 返回内容的MIME类型                                           | Content-Type: text/html; charset=utf-8                |
| Date               | 原始服务器消息发出的时间                                     | Date: Tue, 15 Nov 2010 08:12:31 GMT                   |
| ETag               | 请求变量的实体标签的当前值                                   | ETag: “737060cd8c284d8af7ad3082f209582d”              |
| **Expires**        | 响应过期的日期和时间                                         | Expires: Thu, 01 Dec 2010 16:00:00 GMT                |
| Last-Modified      | 请求资源的最后修改时间                                       | Last-Modified: Tue, 15 Nov 2010 12:45:26 GMT          |
| Location           | 用来重定向接收方到非请求URL的位置来完成请求或标识新的资源    | Location: http://www.zcmhi.com/archives/94.html       |
| Pragma             | 包括实现特定的指令，它可应用到响应链上的任何接收方           | Pragma: no-cache                                      |
| Proxy-Authenticate | 它指出认证方案和可应用到代理的该URL上的参数                  | Proxy-Authenticate: Basic                             |
| refresh            | 应用于重定向或一个新的资源被创造，在5秒之后重定向（由网景提出，被大部分浏览器支持） | Refresh: 5; url=http://www.zcmhi.com/archives/94.html |
| Retry-After        | 如果实体暂时不可取，通知客户端在指定时间之后再次尝试         | Retry-After: 120                                      |
| Server             | web服务器软件名称                                            | Server: Apache/1.3.27 (Unix) (Red-Hat/Linux)          |
| Set-Cookie         | 设置Http Cookie                                              | Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1   |
| Trailer            | 指出头域在分块传输编码的尾部存在                             | Trailer: Max-Forwards                                 |
| Transfer-Encoding  | 文件传输编码                                                 | Transfer-Encoding:chunked                             |
| Vary               | 告诉下游代理是使用缓存响应还是从原始服务器请求               | Vary: *                                               |
| Via                | 告知代理客户端响应是通过哪里发送的                           | Via: 1.0 fred, 1.1 nowhere.com (Apache/1.1)           |
| Warning            | 警告实体可能存在的问题                                       | Warning: 199 Miscellaneous warning                    |
| WWW-Authenticate   | 表明客户端请求实体应该使用的授权方案                         | WWW-Authenticate: Basic                               |

 







## 前后端开发中经常遇到的问题，跨域

#### 一、什么叫跨域（前端层面的理解）？通源策略

首先理解什么情况不跨域：

`相同的协议（http、https）`、`相同的端口`、`相同的host`；

以上三个条件任何一个不满足就叫做跨域，当然满足以上三个情况都是相同的域；

前端层面理解跨域，跨域只存在于浏览器上，浏览器为了安全限制，禁止不同域名之间相互通信；在非浏览器环境下没有跨域；

**浏览器的同源策略**

规定跨域之间的脚本是隔离的，一个域的脚本不能访问和操作另外一个域的绝大部分属性和方法。

1. DOM同源策略：禁止对不同源页面DOM进行操作。这里主要场景是iframe跨域的情况，不同域名的iframe是限制互相访问的。
2. XmlHttpRequest同源策略：禁止使用XHR对象向不同源的服务器地址发起HTTP请求。



 #### 二、如何解决跨域

1. Jsonp

2. Access Control（CORS 跨域资源共享 corss-origin resource sharing）

   > 对于客户端：并不需要做任何操作，正常的发送xhr请求；
   >
   > 唯一需要注意的是：如果需要把cookie带到服务端，需要设置：xhr.withCredentials = true
   >
   > -
   >
   > 对于服务端，需要在response header 中设置如下两个字段：
   >
   > Access-Control-Allow-Origin: [http://www.yourhost.com](https://link.zhihu.com/?target=http%3A//www.yourhost.com)  （这里可以设置为*，允许所有域名访问，但是这样可能会有一些安全方面的问题，具体细节有待研究）
   >
   > Access-Control-Allow-Credentials:true
   >
   > 这样，我们就可以跨域请求接口了；

   学习资料：[阮一峰老师](http://www.ruanyifeng.com/blog/2016/04/cors.html)

3. Window.name

4. Server proxy（使用代理，项目中常用的nginx做代理）

5. document.domain

6. window.postMessage

   > 这是html5定义的一个方法，这个方法更多的是解决不同域名多窗口之间的跨域消息传递；

**跨域为了解决安全问题，相关的也有很多前端安全相关的问题，了解一下（CSRF攻击）**



#### 三、在实际项目中解决跨域最常见的方法：CORS、代理

**CORS详解**

**介绍：**

CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。

浏览器自动实现cors；（浏览器一旦发现AJAX请求跨源，会自动添加一些附加头信息，有时还会多出一次options-预检请求）

CORS接口的实现主要依靠服务端；（如何实现？）

1. 简单请求：

2. 非简单请求



## 问题记录：

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



2. 浏览器缓存问题的理解？

   项目中遇到过，浏览器缓存后端接口的情况；

## 参考链接：

[http，请求头、相应头介绍](https://www.jianshu.com/p/b5993a20292a)

[content-type理解](https://segmentfault.com/a/1190000003002851)

[知乎](https://www.zhihu.com/question/26376773)



## 从http可以延伸到理解一下网络传输方面的东西

1. 短连接、长连接
2. http、tcp、ftp等
3. http的底层传输方式tcp，http1.0；三次握手



## 下周整理：浏览器从输入网址，到页面呈现，其中到底都做了些什么？

