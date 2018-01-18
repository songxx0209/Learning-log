---
title: 浏览器缓存机制
---



浏览器是如何知道使用[缓存](http://caibaojian.com/t/%e7%bc%93%e5%ad%98)的，其实这都是通过http中，浏览器将最后修改时间发送请求给[web](http://caibaojian.com/c/web)服务器，web服务器收到请求后跟服务器上的文档最后修改的时间对比，如果web服务器上最新文档修改时间小于或者等于浏览器发送过来的，则发送304给浏览器，使用[缓存](http://caibaojian.com/t/%e7%bc%93%e5%ad%98)版本。

### cache策略

- 浏览器缓存（http缓存机制）
  - 协商缓存
  - 本地缓存（强制缓存）
- 服务器缓存
  - CDN缓存
  - Combo缓存
- HTML5缓存思路
  - 离线存储manifest
  - 本地存储LocalStorage

[缓存机制文章](http://caibaojian.com/http-cache.html)

| **获取资源形式** | **状态码** | **发送请求到服务器**      |                       |
| ---------- | ------- | ----------------- | --------------------- |
| **强缓存**    | 从缓存取    | 200（from cache）   | 否，直接从缓存取              |
| **协商缓存**   | 从缓存取    | 304（not modified） | 是，正如其名，通过服务器来告知缓存是否可用 |



**关于http缓存的头信息：**

http://caibaojian.com/http-cache.html

Request[·](http://caibaojian.com/http-cache.html)

| Cache-Control: max-age=0                 | 以秒为单位        |
| ---------------------------------------- | ------------ |
| If-Modified-Since: Mon, 19 Nov 2012 08:38:01 GMT | 缓存文件的最后修改时间。 |
| If-None-Match: "0693f67a67cc1:0"         | 缓存文件的Etag值   |
| Cache-Control: no-cache                  | 不使用缓存        |
| Pragma: no-cache                         | 不使用缓存        |



Response[·](http://caibaojian.com/http-cache.html)

| Cache-Control: public                    | 响应被缓存，并且在多用户间共享，  （公有缓存和私有缓存的区别，请看另一节） |
| ---------------------------------------- | -------------------------------------- |
| Cache-Control: private                   | 响应只能作为私有缓存，不能在用户之间共享                   |
| Cache-Control:no-cache                   | 提醒浏览器要从服务器提取文档进行验证                     |
| Cache-Control:no-store                   | 绝对禁止缓存（用于机密，敏感文件）                      |
| Cache-Control: max-age=60                | 60秒之后缓存过期（相对时间）                        |
| Date: Mon, 19 Nov 2012 08:39:00 GMT      | 当前response发送的时间                        |
| Expires: Mon, 19 Nov 2012 08:40:01 GMT   | 缓存过期的时间（绝对时间）                          |
| Last-Modified: Mon, 19 Nov 2012 08:38:01 GMT | 服务器端文件的最后修改时间                          |
| ETag: "20b1add7ec1cd1:0"                 | 服务器端文件的Etag值                           |







如果同时存在cache-control和Expires怎么办呢？

> 浏览器总是优先使用cache-control，如果没有cache-control才考虑Expires

协商缓存是通过什么来判断， 使用缓存？

浏览器如何命中 强制缓存和协商缓存？

[讲解](http://www.cnblogs.com/wonyun/p/5524617.html)

强制缓存：

```
cache-control:max-age=2592000,s-maxage=3600

Status Code:200  (from memory cache)
```



```
Status Code:200  (from disk cache)
```

