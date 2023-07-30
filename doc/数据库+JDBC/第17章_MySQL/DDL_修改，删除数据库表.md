
# DDL_修改，删除数据库表




1.  -- 查看数据：
2.  select * from t_student;
3.  -- 修改表的结构：
4.  -- 增加一列：
5.  alter table t_student add score double(5,2) ; -- 5:总位数  2：小数位数 
6.  update t_student set score = 123.5678 where sno = 1 ;
7.  -- 增加一列（放在最前面）
8.  alter table t_student add score double(5,2) first;
9.  -- 增加一列（放在sex列的后面）
10. alter table t_student add score double(5,2) after sex;
11. -- 删除一列：
12. alter table t_student drop score;
13. -- 修改一列：
14. alter table t_student modify score float(4,1); --
    modify修改是列的类型的定义，但是不会改变列的名字
15. alter table t_student change score score1 double(5,1); -- change修改列名和列的类型的定义
16. -- 删除表：
17. drop table t_student; 






------------------------------------------------------------

