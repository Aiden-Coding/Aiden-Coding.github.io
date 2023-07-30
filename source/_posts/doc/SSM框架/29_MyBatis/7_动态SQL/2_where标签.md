
# 2_where标签

用于处理where关键字和and 




1.  <select id="findEmpByCondition" resultType="emp">
2.      select * from emp
3.      <where>
4.          <if test="empno != null">
5.              and empno= #{empno}
6.          </if>
7.          <if test="ename != null and ename != ''">
8.              and ename= #{ename}
9.          </if>
10.         <if test="job != null and job != ''">
11.             and job= #{job}
12.         </if>
13.         <if test="mgr != null ">
14.             and mgr= #{mgr}
15.         </if>
16.         <if test="hiredate != null ">
17.             and hiredate= #{hiredate}
18.         </if>
19.         <if test="sal != null">
20.             and sal= #{sal}
21.         </if>
22.         <if test="comm != null ">
23.              and comm =#{comm}
24.         </if>
25.         <if test="deptno != null ">
26.             and deptno= #{deptno}
27.         </if>
28.     </where>
29. </select>

 






------------------------------------------------------------

