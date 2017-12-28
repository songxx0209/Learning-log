# shell study

1: 友情链接

- [极客学院shell学习](http://wiki.jikexueyuan.com/project/linux-command/chap05.html)
- ​

2：

```
echo "/usr/local/bin/fish" | sudo tee -a /etc/shells
// 什么意思

```



```
chsh -s /usr/local/bin/fish
```

```
mkdir homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C homebrew

```

修改shell 使用：

```
查看当前发行版可以使用的shell
[jack@localhost ~]$ cat /etc/shells 
/bin/sh
/bin/bash
/sbin/nologin
查看当前使用的shell


cash -s /bin/bash
// 修改默认shell
```

2：brew install mysql  **为命令行设置代理**

- 慢的不得了， 网上查了一下，有说用镜像的， 有说用代理的。

- 最后用了一下代理：（有时间研究一下原理）

  ```
  export ALL_PROXY=socks5://127.0.0.1:1080
  // 让终端也使用代理 下载东西
  ```

  如果说你想要 **brew** 永久如此，我们就需要将环境变量写入终端的配置当中，这取决于你的终端，如果是默认的 **bash**，则写入 ~/.bash_profile ，如果是 **zsh**，则写在 ~/.zshrc  里。

  或者直接用如下语句来将命令直接导入到配置文件里，感谢 surveillance104 的提醒哦！

  ```
  echo export ALL_PROXY=socks5://127.0.0.1:1080 >> ~/.bash_profile

  //如果是zsh就下边这个

  echo export ALL_PROXY=socks5://127.0.0.1:1080 >> ~/.zsh_profile
  ```

  ​

  ​

  这样，**Homebrew** 就能通过 shadowsocks 来更新了，速度嗖嗖的。：）

  ​

3：mysql 下载完成后需要 设置初始密码。

- ```
  brew install mysql

  mysql.server start // 启动mysql服务

  mysql_secure_installation // 修改初始 密码 ， 但是修改不了
  // .. Failed! Error: Your password does not satisfy the current policy requirements
  ```


  解决方法：
1.   命令 mysql -uroot 登录 MySQL
  2. 跑这一句后回车，更改强度为 LOW，LOW 代表什么？代表密码任意，但长度在 8 位或以上。
      你要问我 MEDIUM 这个强度代表什么……代表密码包括：数字、大写字母、小写字母、特殊符号、长度 8 位以上。
      那个 STRONG 我就不解释了。。。
      [sql] view plain copy print?
      set global validate_password_policy=0;  
  3. LOW 强度允许我们设置为纯数字纯字母等密码，但是我们还是不能设置 123456，因为最低要求 8 位，没事，继续跑这一句
      你要问我那个 length 为什么要设置 4，因为不管你设置 1、2、3、4，最低长度都是 4。
      [sql] view plain copy print?
      set global validate_password_length=4; 
  4. 好了，再次运行 mysql_secure_installation，安心的设置 123456 了。。。
  ```

  ```

- ​