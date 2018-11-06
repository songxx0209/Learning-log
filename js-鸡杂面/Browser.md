---
title: 浏览器的工作机制、如何提高浏览器工作效率
---



[参考链接](https://segmentfault.com/a/1190000010298038)

### 用户输入url，到浏览器展示网页的过程

1. 用户输入URL地址
2. 浏览器解析URL解析出主机名
3. 浏览器将主机名转换成服务器ip地址（浏览器先查找本地DNS缓存列表 没有的话 再向浏览器默认的DNS服务器发送查询请求 同时缓存）
4. 浏览器将端口号从URL中解析出来
5. 浏览器建立一条与目标Web服务器的TCP连接（三次握手）
6. 浏览器向服务器发送一条HTTP请求报文
7. 服务器向浏览器返回一条HTTP响应报文
8. 关闭连接 浏览器解析文档
9. 如果文档中有资源 重复6 7 8 动作 直至资源全部加载完毕





## 浏览器的工作机制

浏览器解析  

1、浏览器通过请求的 URL 进行域名解析，向服务器发起请求，接收文件（HTML、CSS、JS、Images等等）。

2、HTML 文件加载后，开始构建 DOM Tree

3、CSS 样式文件加载后，开始解析和构建 CSS Rule Tree

4、Javascript 脚本文件加载后， 通过 DOM API 和 CSSOM API 来操作 DOM Tree 和 CSS Rule Tree



浏览器渲染  

1、浏览器引擎通过 DOM Tree 和 CSS Rule Tree 构建 Rendering Tree

2、Rendering Tree 并不与 DOM Tree 对应，比如像 <head> 标签内容或带有 display: none; 的元素节点并不包括在 Rendering Tree 中 。

3、通过 CSS Rule Tree 匹配 DOM Tree 进行定位坐标和大小，是否换行，以及 position、overflow、z-index 等等属性，这个过程称为 Flow 或 Layout 。

4、最终通过调用Native GUI 的 API 绘制网页画面的过程称为 Paint 。

![](https://upload-images.jianshu.io/upload_images/8133-7a8a0afcd59349d1.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/630)













## 如何避免浏览器的的低效工作

**尽可能少的操作DOM，甚至做到苛刻、吝啬；**

> `Repaint`——屏幕的一部分要重画，比如某个CSS的背景色变了。但是元素的几何尺寸没有变。
>
> `Reflow`——意味着元件的几何尺寸变了，我们需要重新验证并计算Render Tree。是Render Tree的一部分或全部发生了变化。这就是Reflow，或是Layout。（**HTML使用的是flow based layout，也就是流式布局，所以，如果某元件的几何尺寸发生了变化，需要重新布局，也就叫reflow**）reflow 会从<html>这个root frame开始递归往下，依次计算所有的结点几何尺寸和位置，在reflow过程中，可能会增加一些frame，比如一个文本字符串必需被包装起来。

#### 减少reflow和repaint

1. 不要一条一条地修改DOM的样式。与其这样，还不如预先定义好css的class，然后修改DOM的className
2. **把DOM离线后修改。如：**
   - 使用documentFragment 对象在内存里操作DOM
   - **先把DOM给display:none(有一次reflow)，然后你想怎么改就怎么改。比如修改100次，然后再把他显示出来。**
   - **clone一个DOM结点到内存里，然后想怎么改就怎么改，改完后，和在线的那个的交换一下。**
   - **尽可能的修改层级比较低的DOM**。当然，改变层级比较底的DOM有可能会造成大面积的reflow，但是也可能影响范围很小。
   - **为动画的HTML元件使用fixed或absoult的position**，那么修改他们的CSS是不会reflow的。



## 页面渲染优化

1. HTML文档结构层次尽量少，最好不深于六层；
2. 脚本尽量后放，放在前即可；
3. 少量首屏样式内联放在标签内；
4. 样式结构层次尽量简单；
5. 在脚本中尽量减少DOM操作，**尽量缓存访问DOM的样式信息**，避免过度触发回流；
6. 减少通过JavaScript代码修改元素样式，尽量使用修改class名方式操作样式或动画；
7. 动画尽量使用在绝对定位或固定定位的元素上；
8. 隐藏在屏幕外，或在页面滚动时，尽量停止动画；
9. **尽量缓存DOM查找，查找器尽量简洁**；
10. 涉及多域名的网站，可以开启域名预解析

> 缓存DOM：缓存DOM查询的结果
>
> ```
> var body = document.getElementsByTagName();
> ```
>
> 