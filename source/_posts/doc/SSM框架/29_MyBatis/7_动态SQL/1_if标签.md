
# 1_if标签

接口 




1.  public interface EmpMapper2 {
2.     List<Emp> findByCondition(Emp emp);
3.  }

 




映射文件 




1.  <?xml version="1.0" encoding="UTF-8" ?>
2.  <!DOCTYPE mapper
3.          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
4.          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
5.  <mapper namespace="com.msb.mapper.EmpMapper2">
6.  <!--List<Emp> findByCondition(Emp emp);-->
7.      <select id="findByCondition" resultType="emp">
8.          select * from emp where 1=1
9.          <if test="empno != null">
10.             and empno =#{empno}
11.         </if>
12.         <if test="ename != null and ename != ''">
13.             and ename like concat('%',#{ename},'%')
14.         </if>
15.         <if test="job != null and job != ''">
16.             and job =#{job}
17.         </if>
18.         <if test="mgr != null">
19.             and mgr =#{mgr}
20.         </if>
21.         <if test="hiredate != null">
22.             and hiredate =#{hiredate}
23.         </if>
24.         <if test="sal != null">
25.             and sal =#{sal}
26.         </if>
27.         <if test="comm != null">
28.             and comm =#{comm}
29.         </if>
30.         <if test="deptno != null">
31.             and deptno =#{deptno}
32.         </if>
33.     </select>
34. </mapper>

 




测试代码 




1.  public static void main(String[] args) {
2.      SqlSession sqlSession = MyBatisUtil.getSqlSession(false);
3.      EmpMapper2 mapper = sqlSession.getMapper(EmpMapper2.class);
4.      Emp condition =new Emp();
5.     /* condition.setDeptno(20);*/
6.     /* condition.setSal(3000.0);*/
7.     /*condition.setHiredate(new java.sql.Date(81,1,22));*/
8.     condition.setComm(0.0);
9.     condition.setDeptno(20);
10.     List<Emp> emps = mapper.findEmpByCondition(condition);
11.     for (Emp e:emps
12.          ) {
13.         System.out.println(e);
14.     }
15. }

 






------------------------------------------------------------

