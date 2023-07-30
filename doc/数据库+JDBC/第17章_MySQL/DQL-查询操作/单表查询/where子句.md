
# where子句

指定查询条件使用where子句，可以查询符合条件的部分记录。 




1.  -- 查看emp表：
2.  select * from emp;
3.  -- where子句：将过滤条件放在where子句的后面，可以筛选/过滤出我们想要的符合条件的数据：
4.  -- where 子句 + 关系运算符
5.  select * from emp where deptno = 10;
6.  select * from emp where deptno > 10;
7.  select * from emp where deptno >= 10;
8.  select * from emp where deptno < 10;
9.  select * from emp where deptno <= 10;
10. select * from emp where deptno <> 10;
11. select * from emp where deptno != 10;
12. select * from emp where job = 'CLERK'; 
13. select * from emp where job = 'clerk'; -- 默认情况下不区分大小写 
14. select * from emp where binary job = 'clerk'; -- binary区分大小写
15. select * from emp where hiredate < '1981-12-25';
16. -- where 子句 + 逻辑运算符：and 
17. select * from emp where sal > 1500 and sal < 3000;  -- (1500,3000)
18. select * from emp where sal > 1500 && sal < 3000; 
19. select * from emp where sal > 1500 and sal < 3000 order by sal;
20. select * from emp where sal between 1500 and 3000; -- [1500,3000]
21. -- where 子句 + 逻辑运算符：or
22. select * from emp where deptno = 10 or deptno = 20;
23. select * from emp where deptno = 10 || deptno = 20;
24. select * from emp where deptno in (10,20);
25. select * from emp where job in ('MANAGER','CLERK','ANALYST');
26. -- where子句 + 模糊查询：
27. -- 查询名字中带A的员工  -- %代表任意多个字符 0,1,2，.....
28. select * from emp where ename like '%A%' ;
29. -- -任意一个字符
30. select * from emp where ename like '__A%' ;
31. -- 关于null的判断：
32. select * from emp where comm is null;
33. select * from emp where comm is not null;
34. -- 小括号的使用  ：因为不同的运算符的优先级别不同，加括号为了可读性
35. select * from emp where job = 'SALESMAN' or job = 'CLERK' and sal >=1500;
    \-- 先and再or  and > or
36. select * from emp where job = 'SALESMAN' or (job = 'CLERK' and sal >=1500); 
37. select * from emp where (job = 'SALESMAN' or job = 'CLERK') and sal >=1500;

 









------------------------------------------------------------

