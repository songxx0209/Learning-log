## vue组件之间的通信

父组件：

```
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <grandChild :msg="msg" @sxx="forChildPassData"></grandChild>
  </div>
</template>

<script>
import GrandChild from './grandChild';

export default {
  name: 'HelloWorld',
  components: { GrandChild },

  data () {
    return {
      msg: 'father component'
    }
  },
  methods: {
    forChildPassData(msg, num) {
      console.log('msg=', msg, num);
    }
  },
}
</script>
```

子组件：

```
<template>
  <div class="hellos">
    <h1>{{ message }}</h1>
    <router-link to="/login">Go to login</router-link>
    <button @click="handleClick">调用父级方法</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: ['msg'],
  data () {
    return {
      message: 'hello , i am grandChild component'
    }
  },
  methods: {
    handleClick() {
      this.$emit('sxx', 'wowo', 234); // 第一个值props名称、后面都是参数；
    }
  }
  
}
</script>

```





**父组件与子组件传递数据**

- 通过props
- 在父组件调用`this.$children[0]._data`



**子组件与父组件传递数据：**

- 父组件向子组件传递方法， 子组件通过props调用父组件的方法，将值通过参数的形式传给父组件
- 使用`$parent`可以访问父组件的数据





**兄弟组件之间的通信：**

1. 如果通过props来解决的话，可以在两个平行子组件的共同父组件中设定一个data用于储存你要传递的数据，然后两个子组件都通过props连接父组件的这个data，实现一个三方同步。

   父组件将一个数据props赋给两个子组件,并是sync的，子组件watch数据回调。

   事实上，两个平行的组件之间不应该直接通信，否则将会破坏组件的独立性（非要通行，又为了保持组件的独立性，建议使用vuex）

2. 如果通过$dispatch和$broadcast来解决的话，可以dispatch到根组件，然后在broadcast到子组件。
3. 还可以通过vuex来解决，处处数据同步，处处可取。