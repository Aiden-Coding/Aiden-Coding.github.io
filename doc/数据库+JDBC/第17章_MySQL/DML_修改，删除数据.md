
# DML_修改，删除数据

注意事项 

1.关键字，表名，字段名不区分大小写 

2.默认情况下，内容不区分大小写 

3.删除操作from关键字不可缺少 

4.修改，删除数据别忘记加限制条件 










1.  -- 修改表中数据
2.  update t_student set sex = '女' ;
3.  update t_student set sex = '男' where sno = 10 ;
4.  UPDATE T_STUDENT SET AGE = 21 WHERE SNO = 10;
5.  update t_student set CLASSNAME = 'java01' where sno = 10 ;
6.  update t_student set CLASSNAME = 'JAVA01' where sno = 9 ;
7.  update t_student set age = 29 where classname = 'java01';
8.  -- 删除操作：
9.  delete from t_student where sno = 2; 






------------------------------------------------------------

