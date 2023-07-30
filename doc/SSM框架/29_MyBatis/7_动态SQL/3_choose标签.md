
# 3_choose标签

前面的when条件成立 后面的 when就不再判断了 




1.  <select id="findEmpByCondition2" resultType="emp">
2.      select * from emp
3.      <where>
4.          <choose>
5.              <when test="empno != null">
6.                  and empno= #{empno}
7.              </when>
8.              <when test="ename != null and ename != ''">
9.                  and ename= #{ename}
10.             </when>
11.             <when test="job != null and job != ''">
12.                 and job= #{job}
13.             </when>
14.             <when test="mgr != null ">
15.                 and mgr= #{mgr}
16.             </when>
17.             <when test="hiredate != null ">
18.                 and hiredate= #{hiredate}
19.             </when>
20.             <when test="sal != null">
21.                 and sal= #{sal}
22.             </when>
23.             <when test="comm != null ">
24.                 and comm =#{comm}
25.             </when>
26.             <when test="deptno != null ">
27.                 and deptno= #{deptno}
28.             </when>
29.         </choose>
30.     </where>
31. </select>

 






------------------------------------------------------------

