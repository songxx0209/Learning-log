## computed、method、watch详解

[官网参考链接](https://cn.vuejs.org/v2/guide/computed.html)

#### computed vs methods

1. methods

   > 当vue.data中的数据，任何一个发生变更时； methods中的所有方法都会执行一遍

2. computed

   > **计算属性是基于它们的依赖进行缓存的**，只有vue.data中与它（computed中的方法）的数据发生改变时，才会执行computed中的方法； 理解它的缓存；
   >
   > 所以computed能减少不必要的计算；

#### 作用\使用场景：

> 设计它们的初衷是用于简单运算;
>
> 在模板中放入太多的逻辑会让模板过重且难以维护;
>
> 对于任何复杂逻辑，你都应当使用**计算属性**



#### 使用方法：

```
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>
```

```
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

##### [计算属性的 setter](https://cn.vuejs.org/v2/guide/computed.html#%E8%AE%A1%E7%AE%97%E5%B1%9E%E6%80%A7%E7%9A%84-setter)

计算属性默认只有 getter ，不过在需要时你也可以提供一个 setter ：

```
// ...
computed: {
  fullName: {
    // getter
    get: function () {
      return this.firstName + ' ' + this.lastName
    },
    // setter
    set: function (newValue) {
      var names = newValue.split(' ')
      this.firstName = names[0]
      this.lastName = names[names.length - 1]
    }
  }
}
// ...
```





#### computed vs method：

```
<p>Reversed message: "{{ reversedMessage() }}"</p>
```

```
// 在组件中
methods: {
  reversedMessage: function () {
    return this.message.split('').reverse().join('')
  }
}
```

- 结果相同

- computed基于它们的依赖进行**缓存**，只有在它的相关依赖发生改变时才会重新求值

- 为什么需要缓存

  > 假设我们有一个性能开销比较大的的计算属性 **A**，它需要遍历一个巨大的数组并做大量的计算。然后我们可能有其他的计算属性依赖于 **A** 。如果没有缓存，我们将不可避免的多次执行 **A** 的 getter！如果你不希望有缓存，请用方法来替代



#### computed vs watch:

两者的比较首先需要了解，它们的异同；





#### FAQ

1. 计算属性能传递参数吗？
2. 什么情况下使用： method、computed、watch？



