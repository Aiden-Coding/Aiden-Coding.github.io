
# group_by分组

【1】group by : 用来进行分组    

【2】sql展示： 




1.  select * from emp;
2.  -- 统计各个部门的平均工资 
3.  select deptno,avg(sal) from emp; -- 字段和多行函数不可以同时使用
4.  select deptno,avg(sal) from emp group by deptno; --
    字段和多行函数不可以同时使用,除非这个字段属于分组
5.  select deptno,avg(sal) from emp group by deptno order by deptno desc;
6.  -- 统计各个岗位的平均工资
7.  select job,avg(sal) from emp group by job;
8.  select job,lower(job),avg(sal) from emp group by job; 









------------------------------------------------------------

