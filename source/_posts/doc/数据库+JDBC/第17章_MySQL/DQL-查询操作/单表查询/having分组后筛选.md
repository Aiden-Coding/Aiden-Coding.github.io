
# having分组后筛选




1.  -- 统计各个部门的平均工资 ,只显示平均工资2000以上的  - 分组以后进行二次筛选 having
2.  select deptno,avg(sal) from emp group by deptno having avg(sal) > 2000;
3.  select deptno,avg(sal) 平均工资 from emp group by deptno having 平均工资 > 2000;
4.  select deptno,avg(sal) 平均工资 from emp group by deptno having 平均工资 > 2000
    order by deptno desc;
5.  -- 统计各个岗位的平均工资,除了MANAGER
6.  -- 方法1：
7.  select job,avg(sal) from emp where job != 'MANAGER' group by job;
8.  -- 方法2：
9.  select job,avg(sal) from emp group by job having job != 'MANAGER' ;
10. -- where在分组前进行过滤的，having在分组后进行后滤。 






------------------------------------------------------------

