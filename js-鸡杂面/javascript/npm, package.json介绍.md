---
title: npm, package.json介绍
---



##### [阮一峰](http://www.ruanyifeng.com/blog/2016/10/npm_scripts.html)

### Package.json目前使用过的功能：

1: 安装包 依赖管理

2: 脚本管理、执行工具  如：npm run build



### npm

npm 脚本的原理非常简单。每当执行`npm run`，就会自动新建一个 Shell，在这个 Shell 里面执行指定的脚本命令。因此，只要是 Shell（一般是 Bash）可以运行的命令，就可以写在 npm 脚本里面。

由于 npm 脚本就是 Shell 脚本，因为可以使用 Shell 通配符。

> ```
> "lint": "jshint *.js"
> "lint": "jshint **/*.js"
> ```



npm 脚本有一个非常强大的功能，就是可以使用 npm 的内部变量。

首先，通过`npm_package_`前缀，npm 脚本可以拿到`package.json`里面的字段。比如，下面是一个`package.json`。

> ```
> {
>   "name": "foo", 
>   "version": "1.2.5",
>   "scripts": {
>     "view": "node view.js"
>   }
> }
>
> ```

那么，变量`npm_package_name`返回`foo`，变量`npm_package_version`返回`1.2.5`。

> ```
> // view.js
> console.log(process.env.npm_package_name); // foo
> console.log(process.env.npm_package_version); // 1.2.5
> ```



## dependencies字段，devDependencies字段

`dependencies`字段指定了项目运行所依赖的模块，`devDependencies`指定项目开发所需要的模块。

**它们都指向一个对象**。该对象的各个成员，分别由模块名和对应的版本要求组成，表示依赖的模块及其版本范围。

