## git使用分享


### 基本概念

首先理解一下remote（远程）；

```
git clone git@github.com:songxx0209/gitStudy.git

git remote -v
// origin	git@github.com:songxx0209/gitStudy.git (fetch)
// origin	git@github.com:songxx0209/gitStudy.git (push)
```

其次理解一下工作流：

![image-20180501001819158](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501001819158.png)




### 常用命令

```
git clone
git remote
git branch 
git push
git pull
git checkout
git fetch
git merge
```

理解以上常用命令的含义、熟练使用



### 分支的理解

![image-20180501004025365](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501004025365.png)



```
git checkout -b dev
```

![image-20180501004044375](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501004044375.png)

![image-20180501004504676](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501004504676.png)



![image-20180501004536942](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501004536942.png)



**关于分支常用操作：**

创建分支、切换分支、删除分支、合并分支



### 常见使用场景

1. 多人协作开发如何来管理git

   最重要的一点是你每次想要向远端仓库提交代码时，都先拉一下（pull）一下远端代码

   具体操作步骤如下：

   **无冲突操作：**

   ```
   // 当你完成本地开发
   git add .   || git add -A

   git commit -m "你的提交日志信息"

   git pull --rebase <远程主机名> <远程分支名>:<本地分支名>

   // 如果没有冲突，万事大吉；直接push就好了
   git push <远程主机名> <本地分支名>:<远程分支名>
   ```

   **存在冲突的情况：**


   ```
   // 当你完成本地开发
   git add .   || git add -A

   git commit -m "你的提交日志信息"

   git pull --rebase <远程主机名> <远程分支名>:<本地分支名>

   // 此时出现冲突的情况：
   ```

   ![image-20180501011310078](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501011310078.png)

到代码里去解决冲突，然后执行：

![image-20180501011721501](/var/folders/9q/2vzfvky96yzd7nx7htrh8l100000gp/T/abnerworks.Typora/image-20180501011721501.png)



2. 备份代码问题

   使用新建分支的方法来备份代码



### 推荐学习网站：

[廖雪峰git](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

[阮一峰 - Git远程操作详解](http://www.ruanyifeng.com/blog/2014/06/git_remote.html)

[阮一峰 - git命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)



### 最后分享一张图：

![](/Users/sxx/Documents/成长/WechatIMG175.jpeg)