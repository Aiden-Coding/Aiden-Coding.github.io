
# 4_实现DML操作

EmpMapper接口 




1.  /**
2.   * 增加员工信息
3.   * @param emp 存储新增员工信息的Emp对象
4.   * @return 对数据库数据产生影响的行数
5.   */
6.  int addEmp(Emp emp);
7.  /**
8.   * 根据员工编号修改员工姓名的方法
9.   * @param empno 要修改的员工编号
10.  * @param ename 修改之后的新的员工名字
11.  * @return 对数据库数据产生影响的行数
12.  */
13. int updateEnameByEmpno(@Param("empno") int empno,@Param("ename") String
    ename);
14. /**
15.  * 根据员工编号删除员工信息
16.  * @param empno 要删除的员工编号
17.  * @return 对数据库数据产生影响的行数
18.  */
19. int deleteByEmpno(int empno);

 




EmpMapper映射 文件 




1.  <!--int addEmp(Emp emp);-->
2.  <insert id="addEmp" >
3.      insert into emp values(DEFAULT
    ,#{ename},#{job},#{mgr},#{hiredate},#{sal},#{comm},#{deptno})
4.  </insert>
5.  <!--int updateEnameByEmpno(@Param("empno") int empno,@Param("ename") String
    ename);-->
6.  <update id="updateEnameByEmpno" >
7.      update emp set ename =#{ename} where empno =#{empno}
8.  </update>
9.  <!--int deleteByEmpno(int empno);-->
10. <update id="deleteByEmpno" >
11.     delete from emp where empno =#{empno}
12. </update>

 







测试代码 




1.  package com.msb.test;
2.  import com.msb.mapper.DeptMapper;
3.  import com.msb.mapper.EmpMapper;
4.  import com.msb.pojo.Dept;
5.  import com.msb.pojo.Emp;
6.  import org.apache.ibatis.io.Resources;
7.  import org.apache.ibatis.session.SqlSession;
8.  import org.apache.ibatis.session.SqlSessionFactory;
9.  import org.apache.ibatis.session.SqlSessionFactoryBuilder;
10. import org.junit.After;
11. import org.junit.Before;
12. import org.junit.Test;
13. import java.io.IOException;
14. import java.io.InputStream;
15. import java.util.Date;
16. /**
17.  * @Author: Ma HaiYang
18.  * @Description: MircoMessage:Mark_7001
19.  */
20. public class Test3 {
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
32.         sqlSession=factory.openSession();
33.     }
34.     @Test
35.     public void testAddEmp(){
36.         EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
37.         mapper.addEmp(new Emp(null, "TOM", "SALESMAN", 7521, new Date(),
    2314.0, 100.0, 10));
38.         sqlSession.commit();
39.     }
40.     @Test
41.     public void testUpdateEnameByEmpno(){
42.         EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
43.         mapper.updateEnameByEmpno(7938, "TOM");
44.         sqlSession.commit();
45.     }
46.     @Test
47.     public void testDeletByEmpno(){
48.         EmpMapper mapper = sqlSession.getMapper(EmpMapper.class);
49.         mapper.deleteByEmpno(7938);
50.         sqlSession.commit();
51.     }
52.     @After
53.     public void release(){
54.         // 关闭SQLSession
55.         sqlSession.close();
56.     }
57. }

 









------------------------------------------------------------

