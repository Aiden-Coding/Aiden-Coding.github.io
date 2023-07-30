
# 2_sqlSession传递参数的三种方式

1 单个基础数据类型作为参数 

2 多个基础数据类型的map 集合作为参数 

3 引用类型作为参数 




Mapper映射文件 




1.  <?xml version="1.0" encoding="UTF-8" ?>
2.  <!DOCTYPE mapper
3.          PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
4.          "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
5.  <mapper namespace="EmpMapper2">
6.      <!--
7.      参数为一个基本数据类型
8.      根据员工工号查询员工的全部信息,返回单个员工对象
9.      public Emp findByEmpno(int empno);
10.     parameterType 在有参数情况下也是可以省略不写  mybatis 可以根据实际情况自动判断
11.     如果要写parameterType 那么就要写对
12.     在SQL语句上可以使用${}  #{} 代表参数的占位
13.     如果参数是单个基本数据类型,{}中名字可以随便写,见名知意
14.     ${} 代表mybatis底层使用Statment语句对象,参数是以字符串拼接的形式设置
15.     #{} 代表mybatis底层使用的preparedStatment语句对象,参数使用?作为占位符处理
16.     #{} 以后常用
17.     -->
18.     <select id="findByEmpno" resultType="emp" parameterType="int">
19.         select  * from emp where empno = #{empno}
20.     </select>
21.     <!--
22.     参数为map集合
23.     查询指定部门号和指定最低薪资的员工信息
24.     20 号部门 且工资在1500以上的员工信息
25.     public List<Emp> findEmpByDeptnoAndSal(int deptno,double sal);
26.     <  >  最好要进行转译处理,参照HTML转译  w3school在线文档中有转译符号对应规则
27.      Map<String,Object> args=new HashMap<>();
28.         args.put("deptno", 20);
29.         args.put("sal", 1500.0);
30.     #{}中写的是map集合中,参数的键
31.     -->
32.     <select id="findEmpByDeptnoAndSal" resultType="emp" parameterType="map">
33.         select * from emp where deptno = #{deptno} and sal &gt;= #{sal}
34.     </select>
35.     <!--
36.    参数为对象
37.    emp >>>  deptno   sal
38.    参数是我们自定义的类型,那么 #{}中写的是参数的属性名
39.    -->
40.     <select id="findEmpByDeptnoAndSal2" resultType="emp"
    parameterType="emp">
41.         select * from emp where deptno = #{deptno} and sal &gt;= #{sal}
42.     </select>
43. </mapper>

 

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
12. import java.util.HashMap;
13. import java.util.List;
14. import java.util.Map;
15. import java.util.Set;
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
35.     public void testSingleArg(){
36.         // 测试单个基本数据类型作为参数
37.         Emp emp = sqlSession.selectOne("findByEmpno", 7499);
38.         System.out.println(emp);
39.     }
40.     @Test
41.     public void testMapArg(){
42.         // 测试Map集合作为参数
43.         Map<String,Object> args=new HashMap<>();
44.         args.put("deptno", 20);
45.         args.put("sal", 3000.0);
46.         List<Emp> emps = sqlSession.selectList("findEmpByDeptnoAndSal",
    args);
47.         emps.forEach(System.out::println);
48.     }
49.     @Test
50.     public void testEmpArg(){
51.         // 测试Map集合作为参数
52.         Emp arg =new Emp();
53.         arg.setDeptno(10);
54.         arg.setSal(2000.0);
55.         List<Emp> emps = sqlSession.selectList("findEmpByDeptnoAndSal2",
    arg);
56.         emps.forEach(System.out::println);
57.     }
58.     @After
59.     public void release(){
60.         // 关闭SQLSession
61.         sqlSession.close();
62.     }
63. }

 























































































------------------------------------------------------------

