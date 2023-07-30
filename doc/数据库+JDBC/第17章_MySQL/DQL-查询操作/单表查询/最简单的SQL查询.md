
# 最简单的SQL查询




1.  -- 对emp表查询：
2.  select * from emp; -- *代表所有数据
3.  -- 显示部分列：
4.  select empno,ename,sal from emp;
5.  -- 显示部分行：where子句
6.  select * from emp where sal > 2000;
7.  -- 显示部分列，部分行：
8.  select empno,ename,job,mgr from emp where sal > 2000;
9.  -- 起别名：
10. select empno 员工编号,ename 姓名,sal 工资 from emp; -- as 省略，''或者""省略了
11. -- as alias 别名
12. select empno as 员工编号,ename as 姓名,sal as 工资 from emp;
13. select empno as '员工编号',ename as "姓名",sal as 工资 from emp;
14. \-- > 1064 - You have an error in your SQL syntax; check the manual that
    corresponds to your MySQL server version for the right syntax to use near
    '编号,ename as "姓 名",sal as 工资 from emp' at line 1
15. -- 错误原因：在别名中有特殊符号的时候，''或者""不可以省略不写
16. select empno as 员工 编号,ename as "姓 名",sal as 工资 from emp;
17. -- 算术运算符：
18. select empno,ename,sal,sal+1000 as '涨薪后',deptno from emp where sal < 2500;
19. select empno,ename,sal,comm,sal+comm from emp;  -- ？？？后面再说
20. -- 去重操作：
21. select job from emp;
22. select distinct job from emp;
23. select job,deptno from emp;
24. select distinct job,deptno from emp; -- 对后面的所有列组合 去重 ，而不是单独的某一列去重
25. -- 排序：
26. select * from emp order by sal; -- 默认情况下是按照升序排列的
27. select * from emp order by sal asc; -- asc 升序，可以默认不写
28. select * from emp order by sal desc; -- desc 降序
29. select * from emp order by sal asc ,deptno desc; -- 在工资升序的情况下，deptno按照降序排列

 






------------------------------------------------------------

