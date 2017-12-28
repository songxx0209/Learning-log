## linux-解压，压缩命令

centos7 解压总结

1：.压缩文件夹为zip文件

`[root@cgls ]``# zip -r mydata.zip mydata`[?](http://www.jb51.net/os/RedHat/534939.html#)

2.把mydata.zip解压到mydatabak目录里面

`[root@cgls ]``# unzip mydata.zip -d mydatabak`[?](http://www.jb51.net/os/RedHat/534939.html#)

3.mydata01文件夹和mydata02.txt压缩成为mydata.zip

`[root@cgls ]``# zip mydata.zip mydata01 mydata02.txt`[?](http://www.jb51.net/os/RedHat/534939.html#)

4.直接解压mydata.zip文件

`[root@cgls ]``# unzip mydata.zip`[?](http://www.jb51.net/os/RedHat/534939.html#)

5.查看mydata.zip文件里面的内容

`[root@cgls ]``# unzip -v mydata.zip`[?](http://www.jb51.net/os/RedHat/534939.html#)

