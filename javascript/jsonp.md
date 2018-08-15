---
title: 前端安全
---



## CSRF

CSRF，通常称为：跨站请求伪造，英文名 Cross-site request forgery；

**原理：**

[参考链接](https://www.cnblogs.com/hyddd/archive/2009/04/09/1432744.html)                  [segmentfault](https://segmentfault.com/a/1190000007932293)

#### 如何防范：

**referer 验证**

根据HTTP协议,在http请求头中包含一个referer的字段,这个字段记录了该http请求的原地址.通常情况下,执行转账操作的post请求`www.bank.com/transfer.php`应该是点击`www.bank.com`网页的按钮来触发的操作,这个时候转账请求的referer应该是`www.bank.com`.而如果黑客要进行csrf攻击,只能在自己的网站`www.hacker.com`上伪造请求.伪造请求的referer是`www.hacker.com`.所以我们通过对比post请求的referer是不是`www.bank.com`就可以判断请求是否合法.

这种方式验证比较简单,网站开发者只要在post请求之前检查referer就可以,但是由于referer是由浏览器提供的.虽然http协议有要求不能篡改referer的值.但是一个网站的安全性绝对不能交由其他人员来保证.



**token验证**

从上面的样式可以发现,攻击者伪造了转账的表单,那么网站可以在表单中加入了一个随机的token来验证.token随着其他请求数据一起被提交到服务器.服务器通过验证token的值来判断post请求是否合法.由于攻击者没有办法获取到页面信息,所以它没有办法知道token的值.那么伪造的表单中就没有该token值.服务器就可以判断出这个请求是伪造的.





## XSS

XSS（cross-site scripting 跨站脚本攻击）

