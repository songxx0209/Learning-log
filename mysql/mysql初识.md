## mysql 学习记录

```
mysql -u root -p


show databases;

use node;

show tables;

drop table student_info; // 删除表

select * from <表名>;
select * from student_info;

desc <表名>;

insert into student
    -> (name, age, sex)
    -> values
    -> ('xiaoming', 21, '男'); // 添加一条数据
    
创建表格时添加：
create table table1(id int auto_increment primary key,...)
    
    
update student set name='xiao' where id=1; // 修改表中的某一个数据

delete from student where age=21;
```

