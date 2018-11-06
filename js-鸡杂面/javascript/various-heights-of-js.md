---
title: The various heights of the browser
---



[资料图解一](http://www.cnblogs.com/polk6/p/5051935.html)

[慕课网笔记讲解](http://www.imooc.com/article/14516)

js中的宽高：电脑屏幕、浏览器、页面

##首先是电脑屏幕的宽高：  window.screen

```
window.screen.height; //屏幕的高度
window.screen.width; // 屏幕的宽度
// 这里需要注意的时，这个屏幕宽高具体一点其实指的是 浏览器的分辨率；个人电脑为例：分辨率 1440*900
// 所以这里
window.screen.height === 900
window.screen.width === 1440
```

```
window.screen.availWidth; // 屏幕中可用区域的宽度
window.screen.availHeight; // 屏幕中可用区域的高度

window.screen.availTop; // 屏幕中可用区域顶部 距 屏幕顶部的距离；
// 心里面模拟一下mac电脑，win电脑的造型；
```



##其次是浏览器的宽高：

浏览器分为两部分：

- 上面 - 工具栏（标签、输入网址区、网址应用记录区）
- 下面 - 页面区

```
window.outerHeight； // 整个浏览器高度。
window.outerWidth； // 整个浏览器宽度。
```

```
// 浏览器内页面可用高度；此高度包含了水平滚动条的高度(若存在)。
// 可表示为浏览器当前高度去除浏览器边框、工具条后的高度。
window.innerHeight;

// 浏览器内页面可用宽度；此宽度包含了垂直滚动条的宽度(若存在)。
// 可表示为浏览器当前宽度去除浏览器边框后的宽度。
window.innerWidth;
```

```
// 工具栏的高度
window.outerHeight - window.innerHeight
```



##最后是我们常用，也是最复杂的页面中各种宽高：window.document

我们常规的认知：

```
{ header, body } = html 
```

但是在这里有点不同：

```
{ header, body, documentElement:html } = document
```



从宽高的角度思考，包含关系：

- window.inner宽高
  - documentElement
    - body



算了，document中从上往下 - 直接上api：

**documentElement、body**

```
document.documentElement.clientWidth； // 可见区域 html的宽度
document.documentElement.clientHeight； // 可见区域 html的高度
```

```
document.body.clientWidth； // 可见区域 BODY对象宽度
document.body.clientHeight； // 可见区域 BODY对象高度
```



> 这里好好理一下，对body的宽高的理解；
>
> 一个块级元素，没有去设置它css样式的情况下，它的宽度永远是等于浏览器 可视区屏幕的宽度的，不包括滚动条延伸出去的区域；

