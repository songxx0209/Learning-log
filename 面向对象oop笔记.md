# 面向对象OOP

## 例子1

```
function OPP (name, qq){        //工厂方式，构造函数
    //原料
    var person = new Object();
    //加工
    person.name = name;
    person.qq = qq;
    person.showName = function(){
    alert('我的名字是'+this.name);
    };
    person.showQQ = function(){
    alert('我的名字是'+this.qq);
    };
    //出厂
    return person;
}
var person1 = OPP('张三'，'23232323');
var person2 = OPP('李四'，'913581148');
alert(person1.showName == person2.showName);  //返回：false
```

### 缺点

> 1：没有new

> 2：代码效率低/浪费资源----上面代码返回false，person1和person2的showName方法代码是一样的，但是他们两个却不相等；因为他们是创建在2块不同内存里中的东西；所以这种写法如果创建100个person就会重复100遍，开辟100块内存来放相同的东西；

## 例子2

```
function OPP (name, qq){        //构造函数
   
    this.name = name;
    this.qq = qq;
    this.showName = function(){
    alert('我的名字是'+this.name);
    };
}
OPP.prototype.showQQ = function (){
  alert('我的名字是'+this.qq);
}
```

> 所有opp实例共有的部分，用prototype（原型）；将opp函数的showQQ方法放在唯一的一块内存中，大家都到那儿去取；所以大家的这个方法或属性的值都是一样的；

### 个人对一些知识的理解记录

#### 1：constructor

> 1、只有对象obj才会有这个属性；
>
> 2、一个对象实例的constructor属性，指向生成这个实例的构造函数；所以同一个构造函数生成的实例a1，a2。   （a1.constructor === a2.constructor）

[阮一峰，构造函数的继承](http://www.ruanyifeng.com/blog/2010/05/object-oriented_javascript_inheritance.html)
