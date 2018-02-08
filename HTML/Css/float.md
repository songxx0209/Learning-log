# float理解

### 浏览器支持

所有主流浏览器都支持 float 属性。

注释：任何的版本的 Internet Explorer （包括 IE8）都不支持属性值 "inherit"。

### 概念理解：

浮动元素会从普通文档流中脱离，但浮动元素影响的不仅是自己，它会影响周围的元素对齐进行环绕。

[float详细讲解](http://luopq.com/2015/11/08/CSS-float/)

**上面这篇文章讲解很详细，看这个就够了；**



### 清除浮动

**解释：**

> clear属性：确保当前元素的左右两侧不会有浮动元素。

**方法有哪些：**

> 1、在希望清楚浮动的元素后面加一个 空的div元素，并设置 style - clear: both;
>
> 2、父级元素添加overflow: hidden;
>
> 3、使用伪类  :before、:after
>
> ```
> clearfix:{
>     zoom:1; // 兼容IE
> }
> clearfix:after{
>     display:block; content:''; clear:both; height:0; visibility:hidden;
> }
> ```
>
> 