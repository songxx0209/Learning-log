## css盒模型

#### 基本概念：标准模型+IE模型

标准：

![](http://7sby7r.com1.z0.glb.clouddn.com/2015-10-03-css-27.jpg)

IE盒模型：

![](http://7sby7r.com1.z0.glb.clouddn.com/2015-10-03-css-30.jpg)



#### 标准模型和IE模型的区别

Height/width的计算方式不同

标准盒子模型：宽度=内容的宽度（content）+ border + padding + margin

低版本IE盒子模型：宽度=内容宽度（content+border+padding）+ margin

#### CSS如何设置这两种模型

```
box-sizing: content-box; // 默认标准模型
box-sizing: border-box; // IE盒模型
```

#### JS如何设置获取盒模型对应的宽和高

```
dom.style.width/height // 只能获取css内连属性（行间width/height）

dom.currentStyle.widht/height // 获取渲染后的dom元素宽高（比较全面），但是这个只有IE浏览器支持该方法

window.getComputedStyle(dom).width/height // 通用型比较好

dom.getBoundingClientRect().width/height // 返回left, top, width, height四个值
```



#### 实例题（根据盒模型解释边距重叠）



#### BFC（边距重叠解决方案）