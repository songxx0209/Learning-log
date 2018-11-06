# meta标签

**参考链接：**

[微信文章](http://mp.weixin.qq.com/s/5bLOcUPx1LaJAVnuAoeImg)



## 前言

meta标签的组成：meta标签共有两个属性，它们分别是http-equiv属性和name属性，不同的属性又有不同的参数值，这些不同的参数值就实现了不同的网页功能。

## 1、name属性

```
<meta name="参数"content="具体的参数值">
```

[name属性的参数](http://www.haorooms.com/post/html_meta_ds)

### viewport参数的讲解

#### 什么是Viewport

手机浏览器是把页面放在一个虚拟的“窗口”（viewport）中，通常这个虚拟的“窗口”（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。移动版的 Safari 浏览器最新引进了 viewport 这个 meta tag，让网页开发者来控制 viewport 的大小和缩放，其他手机浏览器也基本支持。

```
<meta name=”viewport” content=”width=device-width, initial-scale=1, maximum-scale=1″>
```

>width：控制 viewport 的大小，可以指定的一个值，如果 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。    
>
>height：和 width 相对应，指定高度。
>
>initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
>
>maximum-scale：允许用户缩放到的最大比例。
>
>minimum-scale：允许用户缩放到的最小比例。
>
>user-scalable：用户是否可以手动缩放
>



### keywords（关键字）

说明：keywords用来告诉搜索引擎你网页的关键字是什么。

### description(网站内容描述)

说明：description用来告诉搜索引擎你的网站主要内容。

### robots(机器人向导)

说明：robots用来告诉搜索机器人哪些页面需要索引，哪些页面不需要索引。



## http-equiv属性

