
# DDL和DML的补充

【1】sql展示： 




1.  -- 创建表：
2.  create table t_student(
3.          sno int(6) primary key auto_increment, 
4.          sname varchar(5) not null, 
5.          sex char(1) default '男' check(sex='男' || sex='女'),
6.          age int(3) check(age>=18 and age<=50),
7.          enterdate date,
8.          classname varchar(10),
9.          email varchar(15) unique
10. );
11. -- 添加数据：
12. insert into t_student values
    (null,'张三','男',21,'2023-9-1','java01班','zs@126.com');
13. insert into t_student values
    (null,'李四','男',21,'2023-9-1','java01班','ls@126.com');
14. insert into t_student values
    (null,'露露','男',21,'2023-9-1','java01班','ll@126.com');
15. -- 查看学生表：
16. select * from t_student;
17. -- 添加一张表：快速添加：结构和数据跟t_student 都是一致的
18. create table t_student2
19. as
20. select * from t_student;
21. select * from t_student2;
22. -- 快速添加，结构跟t_student一致，数据没有：
23. create table t_student3
24. as
25. select * from t_student where 1=2;
26. select * from t_student3;
27. -- 快速添加：只要部分列，部分数据：
28. create table t_student4
29. as
30. select sno,sname,age from t_student where sno = 2;
31. select * from t_student4;
32. -- 删除数据操作 :清空数据
33. delete from t_student;
34. truncate table t_student;

 







【2】delete和truncate的区别： 

从最终的结果来看，虽然使用TRUNCATE操作和使用DELETE操作都可以删除表中的全部记录，但是两者还是有很多区别的，其区别主要体现在以下几个方面： 

(1)DELETE为数据操作语言DML；TRUNCATE为数据定义语言DDL。 

(2)
DELETE操作是将表中所有记录一条一条删除直到删除完；TRUNCATE操作则是保留了表的结构，重新创建了这个表，所有的状态都相当于新表。因此，TRUNCATE
作的效率更高。 

(3)DELETE操作可以回滚；TRUNCATE操作会导致隐式提交，因此不能回滚（在第十章中会讲解事务的提交和回滚）。 

(4)DELETE操作执行成功后会返回已删除的行数（如删除4行记录，则会显示“Affected
rows：4”）；截断操作不会返回已删除的行量，结果通常是“Affected
rows：0”。DELETE操作删除表中记录后，再次向表中添加新记录时，对于设置有自增约束字段的值会从删除前表中该字段的最大值加1开始自增；TRUNCATE操作
会重新从1开始自增。 



------------------------------------------------------------

