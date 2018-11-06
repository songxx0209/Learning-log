---
title: Promise理解 并深入理解同步，异步
---



### Promise

**学习一个东西我们首先需要了解它的大体轮廓是什么样的，在来了解一些细节的东西**

#### 首先要理解Promise，它只是一个构造函数，设计目的就是为了使异步操作按照我们想要的顺序来依次执行

![](http://images2015.cnblogs.com/blog/520134/201603/520134-20160311003722741-755677508.png)

```
var ss = () => console.log('woshidiyi');
function run(){
    return new Promise(function(resolve, reject){   //需要将promise对象return出去
        //做一些异步操作
        setTimeout(function(){
            console.log('执行完成');
            resolve('随便什么数据');   //成功后将数据传递给后面的then方法
        }, 2000);
    });          
}
function run1(){
    return new Promise(function(resolve, reject){
        //做一些异步操作
        setTimeout(function(){
            console.log('执行完成1');
            resolve('随便什么数据1');
        }, 2000);
    });          
}
run()
.then(function(data) {
	console.log(data);
	return (function (){
		console.log('sdf1111111111')
		return '我是直接返回的';
	})()
})
.then((data) => console.log('sdf', data))
.then(ss)
```

promise接受一个函数做参数，该函数中传入2参数：resolve，reject，分别可理解为成功，失败；

then可以接受两个回调函数作参数如 fun，  如果是fun() 执行函数，则会马上执行。

> 链式操作，从上往下依次执行，异步操作中上面的函数是promise对象，才会等其执行完了才执行下面的then，如果下面的then中包含的是 -自制行函数或函数执行 "fun()"会同步执行不用等待。

> 想要往下面传值，如果上面是promise对象就只需传值给对象中的resolve（值），如果上面不是promise就只需要return一个数据就可以了

```
run()
.then(function(data) {
	console.log(data);
	return run1();
})
.then((data) => console.log('sssss', data))
// 执行完成
// 随便什么数据
// 执行完成1
// sssss 随便什么数据1
```

```
run()
.then(function(data) {
	console.log(data);
	return run1();
})
.then((data) => console.log('sssss', data))
.then(ss())
// woshidiyi
// 执行完成
// 随便什么数据
// 执行完成1
// sssss 随便什么数据1
```

> 如果上面的函数不是promise对象，异步操作就不会遵守一个一个依次执行的情况

```
run()
.then(function(data) {
	console.log(data);
	setTimeout(function(){
            console.log('0');
        }, 0);
})
.then(function() {
	setTimeout(function(){
            console.log('1');
        }, 4000);
})
.then(function() {
	setTimeout(function(){
            console.log('2');
        }, 1000);
})
// 执行完成
// 随便什么数据
// 0
// 2
// 1
```

#### 还有一些方法后续再查看，如 all，catch，race

## 一个面试题

```
function fun(tag){
	console.log(tag);
	return tag * 10;
}
function funp(tag = 4){
    var p = new Promise(function(resolve, reject){
    	console.log(tag); 
        //做一些异步操作
        setTimeout(function(){
            console.log(tag +1);
            resolve(tag*10);
        }, 2000);
    });
    return p;            
}

funp(2)
.then(funp())
.then(funp(6))
.then(fun())
// 2
// 4
// 6
// undefined
// 3
// 5
// 7
```

> then中的参数 都是执行一个函数，所以变成了依次执行的普通同步操作

# **同步 & 异步**

>```
>console.log('woshi 1');
>console.log('woshi 3');
>setTimeout(() => console.log('woshi***'), 100);
>setTimeout(() => console.log('woshi 4'), 100);
>console.log('woshi 5');
>
>setTimeout(() => console.log('woshi 6'), 6000);
>console.log('woshi 7');
>
>setTimeout(() => console.log('woshi 8'), 7000);
>console.log('woshi 9');
>setTimeout(() => console.log('woshi 2'), 0);
>// woshi 1
>// woshi 3
>// woshi 5
>// woshi 7
>// woshi 9
>// woshi 2
>// woshi***
>// woshi 4
>// woshi 6
>// woshi 8
>```
>
>`在一个代码的运行环境中，首先以从上往下的顺序执行所有的同步操作，中途遇到异步操作会将其放入到异步队列中等待。等到同步操作完成结束，才开始执行异步操作，`所有异步操作可以理解为同时进行`（类似于多线程，但是是不是还需要考证）,根据花费时间的多少来依次返回结果，耗时越少越早返回结果，如果耗时相同则以代码从上往下的先后顺序返回结果。`-----这是一个错误的理解
>
>代码从上往下执行， 只是到异步操作时它会到队列中执行等待并不会阻止后续操作，直到所有同步完成后，才开始返回异步的结果。

