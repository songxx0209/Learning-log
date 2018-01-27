---
title: Regular Expression
---



1. test. 一个在字符串中测试是否匹配的RegExp方法，它返回true或false。

   ```
   var str = 'hello world!';
   var result = /^hello/.test(str);
   console.log(result); // true
   ```

2. match 一个在字符串中执行查找匹配的String方法，它返回一个数组或者在未匹配到时返回null。

   ```
   var str = 'For more information, see Chapter 3.4.5.1';
   var re = /see (chapter \d+(\.\d)*)/i;
   var found = str.match(re);

   console.log(found);

   // logs [ 'see Chapter 3.4.5.1',
   //        'Chapter 3.4.5.1',
   //        '.1',
   //        index: 22,
   //        input: 'For more information, see Chapter 3.4.5.1' ]

   // 'see Chapter 3.4.5.1' 是整个匹配。
   // 'Chapter 3.4.5.1' 被'(chapter \d+(\.\d)*)'捕获。
   // '.1' 是被'(\.\d)'捕获的最后一个值。
   // 'index' 属性(22) 是整个匹配从零开始的索引。
   // 'input' 属性是被解析的原始字符串。
   ```

   ```
   var str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz';
   var regexp = /[A-E]/gi;
   var matches_array = str.match(regexp);

   console.log(matches_array);
   // ['A', 'B', 'C', 'D', 'E', 'a', 'b', 'c', 'd', 'e']
   ```

3. search 一个在字符串中测试匹配的String方法，它返回匹配到的位置索引，或者在失败时返回-1。

   ```
   function testinput(re, str){
     var midstring;
     if (str.search(re) != -1){
       midstring = " contains ";
     } else {
       midstring = " does not contain ";
     }
     console.log (str + midstring + re);
   }
   ```

4. replace 一个在字符串中执行查找匹配的String方法，并且使用替换字符串替换掉匹配到的子字符串。

   ```
   var str = 'Twas the night before Xmas...';
   var newstr = str.replace(/xmas/i, 'Christmas');
   console.log(newstr);  // Twas the night before Christmas...
   ```

5. split 一个使用正则表达式或者一个固定字符串分隔一个字符串，并将分隔后的子字符串存储到数组中的String方法。

   ```
   var names = 'Harry Trump ;Fred Barney; Helen Rigby ; Bill Abel ;Chris Hand ';

   console.log(names);

   var re = /\s*;\s*/;
   var nameList = names.split(re);

   console.log(nameList);
   ```

   ​

## 正则表达式使用总结

#### 如何理解开始、结束 字符：

```
/^ ... $/
eg:

var str = 'Twas the night before Xmas';
var ss = new RegExp(/mas$/, 'g');
var newstr = str.replace(ss, 'Christmas');
console.log(newstr);
// Twas the night before XChristmas
// 匹配结尾的mas

var a = '   asasd   ';
var b = a.replace(/^\s+|\s+$/g,"");
console.log(b);
// asasd
// 替换了开头和结尾的空格
```

有开始和结束符， 匹配`整个字符串`是否匹配 正则规则；



#### 贪婪、非贪婪 匹配

```
var ele = 'This is a <EM>first</EM> test is a <EM>first</EM> test';
var ss = ele.match(/<.+>/);
console.log(ss);
// ["<EM>first</EM> test is a <EM>first</EM>", index: 10, input: "This is a <EM>first</EM> test is a <EM>first</EM> test"]
```

由于`+`的贪婪性，使得正则表达式引擎返回了一个最左边的最长的匹配



如果想得到期望的结果，就需要启用非贪婪模式：`<.+?>`

```
var ele = 'This is a <EM>first</EM> test is a <EM>first</EM> test';
var ss = ele.match(/<.+?>/);
console.log(ss);
// ["<EM>", index: 10, input: "This is a <EM>first</EM> test is a <EM>first</EM> test"]
// 这里精准的匹配了<EM>
// 非贪婪匹配
```

**1.什么是正则表达式的贪婪与非贪婪匹配**

如：String str="abcaxc";

　　Patter p="ab*c";

**贪婪匹配:**正则表达式一般趋向于最大长度匹配，也就是所谓的贪婪匹配。如上面使用模式p匹配字符串str，结果就是匹配到：**abcaxc**(ab*c)。

**非贪婪匹配**：就是匹配到结果就好，就少的匹配字符。如上面使用模式p匹配字符串str，结果就是匹配到：**abc**(ab*c)。

**2.编程中如何区分两种模式**

　　**默认是贪婪模式；在量词后面直接加上一个问号？就是非贪婪模式。**

　　量词：{m,n}：m到n个

　　　　　*：任意多个

　　　　　+：一个到多个

　　　　　？：0或一个