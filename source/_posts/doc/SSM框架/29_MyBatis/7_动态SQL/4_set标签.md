
# 4_set标签

接口 




1.  int updateEmpByCondtion(Emp emp);

 




映射文件 




1.  <!--int updateEmpByCondtion(Emp emp);-->
2.  <update id="updateEmpByCondtion" >
3.      update emp
4.      <set>
5.          <if test="ename != null and ename != '' ">
6.              , ename =#{ename}
7.          </if>
8.          <if test="job != null and ename != '' ">
9.              , job =#{job}
10.         </if>
11.         <if test="mgr != null ">
12.             , mgr =#{mgr}
13.         </if>
14.         <if test="hiredate != null ">
15.             , hiredate =#{hiredate}
16.         </if>
17.         <if test="sal != null ">
18.             , sal =#{sal}
19.         </if>
20.         <if test="comm != null ">
21.             , comm =#{comm}
22.         </if>
23.         <if test="deptno != null ">
24.             , deptno =#{deptno}
25.         </if>
26.     </set>
27.     where empno =#{empno}
28. </update>

 












------------------------------------------------------------

