---
title: 通过github、hexo搭建个人博客流程
---



最简单的方法，google一下标题，方法一大堆；



**说说个人搭建时遇到的一些问题：**

`一：更换主题`



`二：博客内部乱码、标签设置中文等问题`



###三：中途提交文章报错：

```
Error: fatal: unable to access 'https://github.com/songxx0209/songxx0209.github.io.git/': LibreSSL SSL_connect: SSL_ERROR_SYSCALL in connection to github.com:443
```

错误信息大概是说 链接github时出错了，错误代码443

经过一番折腾最终解决：修改hexo配置文件——config.yml中deploy：repo

修改前：

```
deploy:
  type: git
  repo: https://github.com/songxx0209/songxx0209.github.io.git
  branch: master
  message: "ready go"
```

也试过给 https 传输方法加上用户名和密码，但是还是不行

```
repo: https://用户名：密码@github.com/songxx0209/songxx0209.github.io.git
```



最后修改后：

```
deploy:
  type: git
  repo: git@github.com:songxx0209/songxx0209.github.io.git
  branch: master
  message: "ready go"
```

**使用 SSH 的方式传输，success!**

 