## vue 核心思想整理

Vue是一种MVVM框架。

> MVVM 是Model-View-ViewModel 的缩写，它是一种基于前端开发的架构模式，其核心是提供对View 和 ViewModel 的双向数据绑定，这使得ViewModel 的状态改变可以自动传递给 View，即所谓的数据双向绑定。

![](/Users/admin/Downloads/MVVM.png) 



而DOM是数据的一个种自然映射。传统的模式是通过Ajax请求从model请求数据，然后手动的触发DOM传入数据修改页面。Vue中，Directives对view进行了封装，当model里的数据发生变化是，Vue就会通过Directives指令去修改DOM。同时也通过DOM Listener实现对视图view的监听，当DOM改变时，就会被监听到，实现model的改变，实现数据的双向绑定。

自己话总结：

> 常规的前端开发，通过操作DOM来改变视图； 这样操作复杂，容易出错；
>
> vue专注于View 层。它让开发者省去了操作DOM的过程，只需要改变数据;
>
> 1. Vue会通过Dircetives指令，对DOM做一层封装，当数据发生改变会通知指令去修改对应的DOM，数据驱动DOM变化，DOM是数据的一种自然映射
> 2. Vue还会对操作进行监听，当视图发生改变时，vue监听到这些变化，从而改变数据，这样就形成了数据的双向绑定。



