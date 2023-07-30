
# DML_添加数据






注意事项 

1.  int  宽度是显示宽度，如果超过，可以自动增大宽度 int底层都是4个字节 
2.  时间的方式多样  '1256-12-23'  "1256/12/23"  "1256.12.23" 
3.  字符串不区分单引号和双引号 
4.  如何写入当前的时间  now() , sysdate() , CURRENT_DATE() 
5.  char varchar 是字符的个数，不是字节的个数，可以使用binary，varbinary表示定长和不定长的字节个数。 
6.  如果不是全字段插入数据的话，需要加入字段的名字 




1.  -- 查看表记录：
2.  select * from t_student;
3.  -- 在t_student数据库表中插入数据：
4.  insert into t_student values
    (1,'张三','男',18,'2022-5-8','软件1班','123@126.com');
5.  insert into t_student values
    (10010010,'张三','男',18,'2022-5-8','软件1班','123@126.com');
6.  insert into t_student values
    (2,'张三','男',18,'2022.5.8','软件1班','123@126.com');
7.  insert into t_student values
    (2,"张三",'男',18,'2022.5.8','软件1班','123@126.com');
8.  insert into t_student values (7,"张三",'男',18,now(),'软件1班','123@126.com');
9.  insert into t_student values (9,"易烊千玺",'男',18,now(),'软件1班','123@126.com');
10. insert into t_student (sno,sname,enterdate) values (10,'李四','2023-7-5');

 











------------------------------------------------------------

