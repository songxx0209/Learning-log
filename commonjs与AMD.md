# commonjs

JS模块化，是前端工程师向全栈跨进的一大步;

commonjs是用在服务器端的，同步加载，如node.js

nodejs因为模块文件都是存放在磁盘上，加载很快不用考虑异步加载。

require()用来引入外部模块；exports对象用于导出当前模块的方法或变量，唯一的导出口；module对象就代表模块本身

# [AMD](http://www.cnblogs.com/JoannaQ/p/3362588.html)

CommenJs加载是同步的，并不适合在浏览器中加载, AMD异步加载适合与浏览器端；

AMD通过define方法来实现模块

define(id?, dependencies?, factory);

 其中：

- id: 模块标识，可以省略。
- dependencies: 所依赖的模块，可以省略。
- factory: 模块的实现，或者一个JavaScript对象（回调）。


####AMD和CMD的区别：

1.AMD预执行，CMD懒执行：AMD一开始就会加载完所有依赖模块并执行，CMD加载完后等到真正require的时候才会执行(RequireJS 从 2.0 开始，也改成可以延迟执行)

2.CMD 推崇依赖就近，AMD 推崇依赖前置。


```
//CMD

define(function(require, exports, module) {
var a = require('./a')
a.doSomething()
// 此处略去 100 行
var b = require('./b') // 依赖可以就近书写
b.doSomething()
// ... 
})

//AMD

define(['./a', './b'], function(a, b) { // 依赖必须一开始就写好
a.doSomething()
// 此处略去 100 行
b.doSomething()
...
})
```

 3.AMD 的 API 默认是**一个当多个用**，CMD 的 API 严格区分，推崇**职责单一**。比如 AMD 里，require 分全局 require 和局部 require，都叫 require。CMD 里，没有全局 require，而是根据模块系统的完备性，提供 seajs.use 来实现模块系统的加载启动。CMD 里，每个 API 都**简单纯粹**


