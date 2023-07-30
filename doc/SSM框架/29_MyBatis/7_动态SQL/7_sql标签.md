
# 7_sql标签




1.  <sql id="empColumn">empno,ename,job,mgr,hiredate,sal,comm,deptno</sql>
2.  <sql id="baseSelect">select <include refid="empColumn"></include> from
    emp</sql>
3.  <!--List<Emp> findByCondition(Emp emp);-->
4.  <select id="findByCondition" resultType="emp">
5.      <include refid="baseSelect"></include>
6.      <trim prefix="where" prefixOverrides="and">
7.          <if test="empno != null">
8.              and empno =#{empno}
9.          </if>
10.         <if test="ename != null and ename != ''">
11.             <bind name="likePattern" value="'%'+ename+'%'"/>
12.             and ename like #{likePattern}
13.         </if>
14.         <if test="job != null and job != ''">
15.             and job =#{job}
16.         </if>
17.         <if test="mgr != null">
18.             and mgr =#{mgr}
19.         </if>
20.         <if test="hiredate != null">
21.             and hiredate =#{hiredate}
22.         </if>
23.         <if test="sal != null">
24.             and sal =#{sal}
25.         </if>
26.         <if test="comm != null">
27.             and comm =#{comm}
28.         </if>
29.         <if test="deptno != null">
30.             and deptno =#{deptno}
31.         </if>
32.     </trim>
33. </select>

 






------------------------------------------------------------

