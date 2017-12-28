# ansible

1: ansible是什么？

>Ansible 是一个 IT 自动化工具。它能配置系统、部署软件、编排更复杂的 IT 任务，如连续部署或零停机时间滚动更新。

2: google  [andible入门](https://www.gitbook.com/book/ansible-book/ansible-first-book/details)

3:[Ansible中文权威指南](http://ansible-tran.readthedocs.io/en/latest/docs/intro_installation.html)



### 安装 ansible

> for mac:
>
> 使用 pip 安装： pip install sensible

### 本地使用ssh无密码链接服务器（远程主机）

首先在本地生成 ssk：

```
$ ssh-keygen
```

运行结束以后，在$HOME/.ssh/目录下，会新生成两个文件：id_rsa.pub和id_rsa。前者是你的公钥，后者是你的私钥。

这时再输入下面的命令，将公钥传送到远程主机host上面：

```
$ ssh-copy-id user@host
```

好了，从此你再登录，就不需要输入密码了。

### 尝试我们的第一个ansible命令

##### 首先需要设置我们的ansible管理哪些主机

什么是 Host Inventory （主机清单）？

Host Inventory 是配置文件，用来告诉Ansible需要管理哪些主机。并且把这些主机根据按需分类。

可以根据用途分类：数据库节点，服务节点等；根据地点分类：中部，西部机房。

##### Host Inventory 配置文件：

默认的文件是： **/etc/ansible/hosts**

如果没有这个目录和文件，请自行创建；

当然也可以修改为其它的文件

> 然后我进行了对hosts文件最简单的配置
>
> Hosts
>
> ```
> 120.77.33.107
> ```
>
> 在hosts文件中配置了我的服务器ip；
>
> 然后在本地终端运行：
>
> ```
> $ansible all -m ping -u root
> // 这里root 是链接远程主机的用户名
> ```
>
> Success!

##### 带分类的hosts文件:

```
mail.example.com

[webservers]
foo.example.com
bar.example.com

[dbservers]
one.example.com
two.example.com
three.example.com
```

可以通过

```
ansible webserver -m ping -vvv
```

ping webserver下的所有主机



#### 拷贝文件

拷贝文件/etc/host到远程主机（组）web，位置为/tmp/hosts

`$ ansible web -m copy -a "src=/etc/hosts dest=/tmp/hosts"`