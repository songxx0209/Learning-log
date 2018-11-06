---
title: web性能优化总结
---



#### 提升也面性能的方法有哪些？

1. 资源压缩合并，减少http请求

2. 非核心代码异步加载：异步加载的方式、异步加载的区别

3. 利用浏览器缓存：缓存的分类、缓存的区别

4. 使用CDN

5. 预解析DNS

   ```
   <meta http-equiv="x-dns-prefetch" content="on"> // 强制打开a标签dns预解析
   <link rel="dns-prefetch" href="//host_name_to_prefetch.com">
   ```

6. 图片处理



### 异步加载

defer

表示脚本可以延迟到文档完全被解析和显示之后再执行。

如果是多个，按照加载的顺序依次执行；

async

加载完成之后立即执行；

如果是多个，执行顺序和加载顺序无关。



### 浏览器缓存

- 强制缓存

  

- 协商缓存

Size：from memory cache、from disk cache