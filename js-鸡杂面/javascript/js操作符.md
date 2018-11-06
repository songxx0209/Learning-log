---
title: js操作符
---



**问题一：**

```
++ 'bb';
// Uncaught ReferenceError: Invalid left-hand side expression in prefix operation
```

```
var a = 'hello';
var b = ++a;
// b : NAN
```

上面为什么报错？

直接写 ++ 字符串，都会报错，但是把字符串保存在一个变量里面再执行++ 就不会报错；



**++、--、-、+操作符：**

```
var a = '1';
var b = ++a; // b: 2; a: 2;
var c = 3;
b = c--; // b: 3; c: 2;
```

**连续 = 的执行方向：**

```
var x = 1;
y = x = typeof y;
// y: 'undefined'
```

> y = x = typeof y;
>
> 是从右往左执行的；先执行x = typeof y；此时，y是为定义undefined，所以x被赋值为undefined；最后x又赋值给y；所以最后y：undefined


```
var x = 1;
var y = '23';
y = x = typeof y;
// y: 'string'
```



**&&、||**

```
var a = x && y;
var b = m || n;
// 执行顺序都是从左往右的执行；返回值并非一定是boolean值；

var a = {name: 'bob'};
var b = a && true; // b: {name: 'bob'} 返回一个对象
```



**/、*、%**

除、乘、求余



**<、>、=**

两个字符串比较，比较的是对应的字符编码值；（一般比较字符串首 个元素 的字符编码值）

