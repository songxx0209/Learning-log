---
title: this - call, apply, bind - new操作符
---



学过bind()\apply()\call()函数的都应该知道，它接收的第一个参数即是上下文对象并将其赋给this。

call 和 apply 都是为了改变某个函数运行时的 context 即上下文而存在的，换句话说，就是为了改变函数体内部 this 的指向。因为 JavaScript 的函数存在「定义时上下文」和「运行时上下文」以及「上下文是可以改变的」这样的概念。

> var func1 = function(arg1, arg2) {};

就可以通过 func1.call(this, arg1, arg2); 或者 func1.apply(this, [arg1, arg2]); 来调用。其中 this 是你想指定的上下文，他可以任何一个 JavaScript 对象(JavaScript 中一切皆对象)，call 需要把参数按顺序传递进去，而 apply 则是把参数放在数组里。



```
obj.call(thisObj, arg1, arg2, ...);
obj.apply(thisObj, [arg1, arg2, ...]);

```

两者作用一致，都是把obj(即this)绑定到thisObj，这时候thisObj具备了obj的属性和方法。或者说thisObj『继承』了obj的属性和方法。

唯一区别是apply接受的是数组参数，call接受的是连续参数。

[js笔记——call,apply,bind使用笔记](https://link.zhihu.com/?target=http%3A//www.cnblogs.com/52fhy/p/5118877.html)



##### 函数在哪里调用才决定了this到底引用的是啥

##### 函数在什么环境里被调用，this就只向这个环境；（不使用call, apply, bind的情况）



