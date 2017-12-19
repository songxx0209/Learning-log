# class、装饰器

> 什么是类（class）， 如何使用，场景，注意事项；
>
> 什么是装饰器，如何使用，场景，注意事项；
>
> 类 和 装饰器之间的联系；

## 类 - class

随着互联网行业的快速发展，程序员需要面对的业务、展示场景也越来越复杂；在这种情况下需要编写维护的代码量也是相当庞大的一个数字；那如何来维护这么庞大的代码呢？

人们常用的方式是模块化；业界中常使用的方法是“面向对象编程”；但是javascript在`ES6`之前是不支持类（class）的；所以才在ES6中提出类`class`的概念；

**ES5之前，Javascript定义类（class）的三种方法**

[阮一峰es6之前创建类的方法](http://www.ruanyifeng.com/blog/2012/07/three_ways_to_define_a_javascript_class.html)

### ES6种class

ECMAScript 2015 中引入的 JavaScript 类(`classes`) 实质上是 JavaScript 现有的基于原型的继承的语法糖。 类语法不是向JavaScript引入一个新的面向对象的继承模型。JavaScript类提供了一个更简单和更清晰的语法来创建对象并处理继承。

`static` 关键字用来定义一个类的一个静态方法。调用静态方法不需要[实例化](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript#The_object_(class_instance))该类，但不能通过一个类实例调用静态方法。静态方法通常用于为一个应用程序创建工具函数。

`extends` 关键字在类声明或类表达式中用于创建一个类作为另一个类的一个子类。