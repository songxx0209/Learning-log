# ssh基本操作和理解

[SSH, The Secure Shell](http://book.douban.com/subject/2299605/)

```
$ ssh-keygen
// 在本地生成公钥和私钥
```

运行结束以后，在$HOME/.ssh/目录下，会新生成两个文件：id_rsa.pub和id_rsa。前者是你的公钥，后者是你的私钥。

这时再输入下面的命令，将公钥传送到远程主机host上面：

```
$ ssh-copy-id user@host
```

好了，从此你再登录，就不需要输入密码了。



1. 场景：本地，远端gitlab，服务器之间代码传输

   **首先本地和远端gitlab之间代码传输：**

   - 当本地向gitlab提交代码时，会要求输入用户名和密码；有user和password当时是可以向远端提交代码的；但是这样的方式会特别麻烦，每次提交代码都需要输入密码；

     所以可以采用无密码提交代码的方式；在本地生成一个ssh-key，然后将本地的sskey保存到远端gitlab上就可以免输入密码提交代码了；

   **服务器 和 gitlab之间代码传输：**

   - 首先是从本地登陆服务器

     ```
     ssh-add
     ssh root@10.112.65.121 -A
     ```

     以上操作能将本地的 免密码提交代码到gitlab的功能带到服务器上；

     `ssh-add`命令是把专用密钥添加到ssh-agent的高速缓存中。

   ​

