
# 5_trim标签

		

1.  Trim 标签处理 set 
2.  			
3.  		 
1.  
    
2.  <update id="updateEmpByCondition2" >
3.      update emp
4.      <!--prefix 要增加什么前缀
5.      prefixOverrides 要去除什么前缀
6.      suffix 要增加什么后缀
7.      suffixOverrides 要去除什么后缀
8.      set 是trim的一种特殊情况
9.      -->
10.     <trim prefix="set"  suffixOverrides="," >
11.         <if test="ename != null and ename != ''">
12.             ename= #{ename},
13.         </if>
14.         <if test="job != null and job != ''">
15.             job= #{job},
16.         </if>
17.         <if test="mgr != null ">
18.             mgr= #{mgr},
19.         </if>
20.         <if test="hiredate != null ">
21.             hiredate= #{hiredate},
22.         </if>
23.         <if test="sal != null">
24.             sal= #{sal},
25.         </if>
26.         <if test="comm != null ">
27.             comm =#{comm},
28.         </if>
29.         <if test="deptno != null ">
30.             deptno= #{deptno},
31.         </if>
32.     </trim>
33.     where  empno = #{empno}
34. </update>

 

Trim标签  处理**where** 

1.  
    
2.  <select id="findEmpByCondition" resultType="emp">
3.      select * from emp
4.          <trim prefix="where" prefixOverrides="and">
5.              <if test="empno != null">
6.                  and empno= #{empno}
7.              </if>
8.              <if test="ename != null and ename != ''">
9.                  and ename= #{ename}
10.             </if>
11.             <if test="job != null and job != ''">
12.                 and job= #{job}
13.             </if>
14.             <if test="mgr != null ">
15.                 and mgr= #{mgr}
16.             </if>
17.             <if test="hiredate != null ">
18.                 and hiredate= #{hiredate}
19.             </if>
20.             <if test="sal != null">
21.                 and sal= #{sal}
22.             </if>
23.             <if test="comm != null ">
24.                 and comm =#{comm}
25.              </if>
26.             <if test="deptno != null ">
27.                 and deptno= #{deptno}
28.             </if>
29.         </trim>
30. </select>

 






------------------------------------------------------------

