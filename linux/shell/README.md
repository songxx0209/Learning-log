### 问题：

1. linux shell操作中可以使用正则表达式吗？

   ```
   cp [file1-file2].extension  destination
   ```

   估计啊，`[]`中是正则表达式吧应该。没错，证明如下：

   ```
   touch a.txt aa.txt
   cp [a-z].txt temp/
   ls temp (    SHOW a.txt)
   ```




## vi/vim 基本操作

