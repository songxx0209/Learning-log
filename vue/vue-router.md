# vue-router使用记录

[参考链接](https://segmentfault.com/a/1190000011122991)



使用路由嵌套是遇到一个奇怪的bug，嵌套路由组件无法加载出来；

### 实现嵌套路由有两个要点：

- 在组件内部使用<router-view>标签
- 在路由器对象中给组件定义子路由

```
{
    path: '/', component: Login,
      children: [
        {
          path: 'home',
          component: home,
        },
        {
          path: 'test',
          component: test,
        },
      ],
}
```



```
// login.vue组件
<div id="app">
  <router-view></router-view>
</div>
```

只有将`router-view`放到login组件内，才能加载子路由的组件；