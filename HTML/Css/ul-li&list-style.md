# ul, li

一般在什么情况下使用

> 多个区域样式风格相同的情况；竖排如拉勾网职位列表[拉钩](https://www.lagou.com/jobs/list_web%E5%89%8D%E7%AB%AF?px=new&city=%E6%88%90%E9%83%BD#order)

```
ul, ol {
  margin: 0;
  padding: 0;
  list-style: none;
}
* {
  outline: 0;
}

```

竖排这样就ok， 去掉li标签前的圆点；ul是行间元素；

#####list-style

```
ul {
  list-style:square inside url('/i/arrow.gif');
}
```

可以按顺序设置如下属性：

- list-style-type
- list-style-position
- list-style-image

可以不设置其中的某个值，比如 "list-style:circle inside;" 也是允许的。未设置的属性会使用其默认值。

| 值                     | 描述                                       |
| --------------------- | ---------------------------------------- |
| *list-style-type*     | 设置列表项标记的类型。参阅：[list-style-type](http://www.w3school.com.cn/cssref/pr_list-style-type.asp) 中可能的值。 |
| *list-style-position* | 设置在何处放置列表项标记。参阅：[list-style-position](http://www.w3school.com.cn/cssref/pr_list-style-position.asp) 中可能的值。 |
| *list-style-image*    | 使用图像来替换列表项的标记。参阅：[list-style-image](http://www.w3school.com.cn/cssref/pr_list-style-image.asp) 中可能的值。 |
| inherit               | 规定应该从父元素继承 list-style 属性的值。              |

```
list-style:list-style-type list-style-position list-style-image;
```

