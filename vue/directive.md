## directive详解

[官网链接](https://cn.vuejs.org/v2/guide/custom-directive.html)

#### 思考：

- directive的使用场景，什么时候应该使用它？
- ​

#### directive - 自定属性

> 有些情况下你依然需要对普通DOM元素进行底层操作，这时候就需要使用自定义属性；



**列子：**

```
<template>
  <div>
    <input v-focus>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      msg: 'Welcome to phicomm',
    };
  },
  directives: {
    focus: {
      // 指令的定义
      inserted: function (el) {
        el.focus()
      }
    }
  },
};
</script>
```

自定义指令，组件加载时input输入框自动获取焦点；



