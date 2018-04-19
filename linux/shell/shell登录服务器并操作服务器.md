## shell expect

[参考链接](https://www.jianshu.com/p/d4c1ac10204d)

[参考链接一](https://blog.csdn.net/Jerome_s/article/details/77351507)

### download

```
brew install expect
```



业务场景：当我们每次需要交互式登录服务器，输入账号密码在服务器上执行机械化操作的时候，经常需要进行繁琐的脚本操作，如果可以写一个脚本自动化执行交互式命令就好了。

```
#!/usr/bin/expect

set timeout 5    
set hostno [lindex $argv 0]    

spawn scp ~/.ssh/id_dsa.pub impala$hostno:~/.ssh/pub_key    
expect "*password*"    
send "111111\r"    

spawn ssh impala$hostno "cat ~/.ssh/pub_key/ >> ~/.ssh/authorized_keys"    
expect "*password*"    
send "111111\r"    

spawn ssh impala$hostno "chmod 600 ~/.ssh/authorized_keys"    
expect "*password*"    
send "111111\r"    

expect eof    
```

分成三个spawn阶段执行不同的操作；