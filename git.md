# git使用经历

个人github账号密码： songxx0209  s1...9x

1：新建一个文件夹，执行git init； 想要克隆远端的其中一个分支？

```
$ git clone -b <branch> <remote_repo>  
// git clone -b 指定的分支名字
// <branch> 表示分支名字 ，如 song-dev
// <remote_repo> 远端repo地址，如：http://10.112.2.3/songxx/resource-ratio.git
// 实例如下：
$ git clone -b song-dev http://10.112.2.3/songxx/resource-ratio.git
```

2：如何理解分支， 本地分支，远端fork分支，upstream分支；

- 本地

  创建一个名为 ' song-dev ' 本地分支

```
git checkout -b song-dev master
// 然后修改 工作区 内容
git add -u      //添加修改文件到缓存区
git commit -m "submit message"  // 将修改文件提交到 本地仓库
git push origin song-dev  // 在远端新建名为song-dev的分支，并将本地仓库 song-dev推送到远端的song-dev
```

现在远端 和 本地 就都有 master 和 song-dev分支，并且他们的内容是对应相同的。

```
git branch -v  // 查看本地有哪些分支？

// 如果去clone 一个远端，会把它所有的分支信息全克隆下来吗？
```

3：在实际开发一个项目中，开发过程中想要提交代码，该怎么操作？

- 首先在提交代码前需要更新一下远端的代码；

  ```
  git remote -v  // 查看本地保存的 远端主机名和网址

  $ git remote add <主机名> <网址>  // 用于添加远程主机

  $ git remote rm <主机名>   // 用于删除远程主机。

  $ git remote rename <原主机名> <新主机名>  // 用于远程主机的改名。

  git pull --rebase upstream master  // 将`远端主机upstream`的内容更新到 本地的master内
  // 看看会不会有冲突， 有冲突就在这里解决；
  // 然后就是一系列的常规操作
  git add -u    git commit -m ""   git push <远程主机名> <本地分支名>:<远程分支名>
  ```

  ​
