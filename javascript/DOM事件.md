## DOM事件

### 基本概念：DOM事件的级别

1. DOM0      element.onclick = function() {}

2. DOM2.     Element.addEventListener('click', function(){}, false)

   > 

3. DOM3.     Element.addEventListener('keyup', function() {}, false)

   > 新增了很多事件，鼠标、键盘事件等



### DOM事件类

**一、事件模型：**

> 捕获
>
> 冒泡

**二、事件流**

> 当用户点击按钮，事件流的过程：
>
> 1. 捕获阶段：事件从上往下传递
> 2. 目标阶段：事件传递到目标元素
> 3. 冒泡阶段：事件从目标元素向上传递

**描述DOM事件捕获的具体流程**

window - document - html - body - .............目标元素

**Event对象的常见应用：**

enent.preventDefault() //组织默认事件

event.stopPropagation() // 阻止冒泡

event.stopImmediatePropagation() // 事件享有优先级

event.currentTarget // 事件代理中使用，

event.target // 事件代理中使用，当前被点击的元素

**自定义事件：**

```
var eve = new Event('custome');

// ev 是一个dom节点
ev.addEventListener('', function() {
    console.log('custome');
});
ev.dispatchEvent(eve);
```

`CustomEvent`相对于event它可以多设置一个参数，用法是相同的；















## 延伸问题：

如何获取html标签？

document.documentElement

1. document.getElementsByTagName(“html”)[0]
2. document.querySelector(“html”);
3. document.body.parentNode;
4. $(‘html’).outerHTML()

