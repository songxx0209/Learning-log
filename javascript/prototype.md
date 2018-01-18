---
title: 理解-函数、构造函数、实例、原型、原型链等概念
---



#### 构造函数创建对象

我们先使用构造函数创建一个对象：

```
function Person() {

}
var person = new Person();
person.name = 'Kevin';
console.log(person.name) // Kevin
```

在这个例子中，Person 就是一个构造函数，我们使用 new 创建了一个实例对象 person。



#### prototype    n. 原型；标准，模范

