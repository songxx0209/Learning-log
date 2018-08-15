## js运行机制

#### js是单线程的

js同一时间，只做一件事情；



#### 什么是任务队列

同步任务，异步任务

同步任务完成之后，再执行异步队列中的任务



#### 异步任务

- setTimeout和setInterval
- DOM事件
- ES6中的Promise



```
console.log(1);
setTimeout(function () {
    console.log(3);
}, 0);
console.log(2);
```

