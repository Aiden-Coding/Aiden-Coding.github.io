
# 3_sqlSession完成DML所有操作

Mapper映射文件 




1.  <?xml version="1.0" encoding="UTF-8" ?>
2.  <!DOCTYPE mapper
3.          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
4.          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
5.  <mapper namespace="EmpMapper3">
6.      <!--
7.      增删方法的返回值类型都是int
8.      resultType就无需指定了
9.      insert update delete 标签中没有resultType
10.     但是仍然可以有paramaterType
11.     -->
12.     <!-- 增加方法
13.     public int addEmp(Emp emp);
14.     -->
15.     <insert id="addEmp" parameterType="emp">
16.         insert into emp
    values(#{empno},#{ename},#{job},#{mgr},#{hiredate},#{sal},#{comm},#{deptno})
17.     </insert>
18.     <!--修改
19.     根据工号修改员工姓名
20.     public int updateEmp(Emp emp);
21.     -->
22.     <update id="updateEmp" parameterType="emp">
23.         update emp set ename = #{ename} where empno=#{empno}
24.     </update>
25.     <!-- 删除
26.     删除大于给定工号的员工信息
27.     public int deleteEmp(int empno)
28.     -->
29.     <delete id="deleteEmp" parameterType="int">
30.         delete from emp where empno >= #{empno}
31.     </delete>
32. </mapper>

 

测试代码 







1.  package com.msb.test;
2.  import com.msb.pojo.Emp;
3.  import org.apache.ibatis.io.Resources;
4.  import org.apache.ibatis.session.SqlSession;
5.  import org.apache.ibatis.session.SqlSessionFactory;
6.  import org.apache.ibatis.session.SqlSessionFactoryBuilder;
7.  import org.junit.After;
8.  import org.junit.Before;
9.  import org.junit.Test;
10. import java.io.IOException;
11. import java.io.InputStream;
12. import java.util.Date;
13. import java.util.HashMap;
14. import java.util.List;
15. import java.util.Map;
16. /**
17.  * @Author: Ma HaiYang
18.  * @Description: MircoMessage:Mark_7001
19.  */
20. public class Test4 {
21.     private SqlSession sqlSession;
22.     @Before
23.     public void init(){
24.         SqlSessionFactoryBuilder ssfb =new SqlSessionFactoryBuilder();
25.         InputStream resourceAsStream = null;
26.         try {
27.             resourceAsStream =
    Resources.getResourceAsStream("sqlMapConfig.xml");
28.         } catch (IOException e) {
29.             e.printStackTrace();
30.         }
31.         SqlSessionFactory factory=ssfb.build(resourceAsStream) ;
32.         sqlSession=factory.openSession(true);
33.     }
34.     @Test
35.     public void testInsert(){
36.         Emp emp =new Emp(null,"按住啦Baby","SALESMAN",7839,new Date(),3100.0,
    200.0,10 );
37.         int rows = sqlSession.insert("addEmp", emp);
38.         System.out.println(rows);
39.         // 手动提交事务
40.         //sqlSession.commit();
41.         /*增删改 要提交事务
42.         * sqlSession.commit();手动提交事务
43.         * sqlSession=factory.openSession(true); 设置事务自动提交
44.         * */
45.     }
46.     @Test
47.     public void testUpdate(){
48.         Emp emp =new Emp( );
49.         emp.setEname("晓明");
50.         emp.setEmpno(7937);
51.         int rows = sqlSession.update("updateEmp", emp);
52.         System.out.println(rows);
53.     }
54.     @Test
55.     public void testDelete(){
56.         int rows = sqlSession.delete("deleteEmp", 7936);
57.         System.out.println(rows);
58.     }
59.     @After
60.     public void release(){
61.         // 关闭SQLSession
62.         sqlSession.close();
63.     }
64. }

 




















































































------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
