# nginx

1. 如何查看 linux上，正在运行的nginx在哪个位置？

2. nginx的配置文件，如何写，常规写法

3. nginx修改配置文件之后需要 重启服务；

   ```
   /usr/local/nginx/sbin/nginx -s reload
   ```

   ```
   server {
     location / {
               root   html;   #这里这个路径 需要执行权限，不要设置到~/目录下
               index  index.html index.htm;
           }
   }
   ```

   ​

4. cp命令

   ```
   cp file1 file2 // 复制file1到file2

   // 复制文件夹
   cp -r A B
   ```

   ​