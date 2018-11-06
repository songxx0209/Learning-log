# border

```
border: border-width border-style border-color;

一般 我常用写法
border: 1px solid #333;
```

#### border-width

```
border-width:thin medium thick 10px;
```

- 上边框是细边框
- 右边框是中等边框
- 下边框是粗边框
- 左边框是 10px 宽的边框

| 值        | 描述              |
| -------- | --------------- |
| thin     | 定义细的边框。         |
| medium   | 默认。定义中等的边框。     |
| thick    | 定义粗的边框。         |
| *length* | 允许您自定义边框的宽度。    |
| inherit  | 规定应该从父元素继承边框宽度。 |



#### border-style

```
border-style:dotted solid double dashed; 
```

- 上边框是点状
- 右边框是实线
- 下边框是双线
- 左边框是虚线

| 值       | 描述                                       |
| ------- | ---------------------------------------- |
| none    | 定义无边框。                                   |
| hidden  | 与 "none" 相同。不过应用于表时除外，对于表，hidden 用于解决边框冲突。 |
| dotted  | 定义点状边框。在大多数浏览器中呈现为实线。                    |
| dashed  | 定义虚线。在大多数浏览器中呈现为实线。                      |
| solid   | 定义实线。                                    |
| double  | 定义双线。双线的宽度等于 border-width 的值。            |
| groove  | 定义 3D 凹槽边框。其效果取决于 border-color 的值。       |
| ridge   | 定义 3D 垄状边框。其效果取决于 border-color 的值。       |
| inset   | 定义 3D inset 边框。其效果取决于 border-color 的值。   |
| outset  | 定义 3D outset 边框。其效果取决于 border-color 的值。  |
| inherit | 规定应该从父元素继承边框样式。                          |

#### border-color

和前面两个一样的规则，只是是设置颜色的；

