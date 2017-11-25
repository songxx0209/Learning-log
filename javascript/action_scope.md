# js 作用域

在[《JavaScript深入之词法作用域和动态作用域》](https://github.com/mqyqingfeng/Blog/issues/3)中讲到，函数的作用域在函数定义的时候就决定了。

## 作用域

作用域是指程序源代码中定义变量的区域。

作用域规定了如何查找变量，也就是确定当前执行代码对变量的访问权限。

JavaScript 采用词法作用域(lexical scoping)，也就是静态作用域。

### 词法作用域

- 变量声明提升机制， 函数内部定义的变量，会提升占位； 在定义前使用变量则为undefined；

- 什么叫变量提升

  变量声明，不管在哪里发生（声明），都会在任意代码执行前处理

  ```
  var value = 1;

  function foo() {
      console.log(value);
  }

  function bar() {
      var value = 2;
      foo();
  }

  bar();

  // 结果是 1
  ```

  ```
  var scope = "global scope";
      function checkscope(){
          var scope = "local scope";
          function f(){
              console.log(scope);
          }
          return f;
      }
      checkscope()(); // local scope
  ```

  ​

  词法作用域就是 静态作用域；

  **原因也很简单，因为JavaScript采用的是词法作用域，函数的作用域基于函数创建的位置。**

  ```
  (function(){
    var a = b = 3;
  })();

  console.log(a); // undefined
  console.log(b); // 3

  // 可以理解为
  (function(){
    b = 3;
    var a = b;
  })();
  ```

  ​