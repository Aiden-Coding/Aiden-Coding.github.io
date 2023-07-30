
# 12_BaseDao抽取

BaseDAO代码 




1.  package com.msb.dao;
2.  import com.msb.pojo.Emp;
3.  import java.lang.reflect.Field;
4.  import java.sql.*;
5.  import java.util.ArrayList;
6.  import java.util.List;
7.  /**
8.   * @Author: Ma HaiYang
9.   * @Description: MircoMessage:Mark_7001
10.  */
11. public abstract class BaseDao {
12.     private static String driver ="com.mysql.cj.jdbc.Driver";
13.     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
14.     private static String user="root";
15.     private static String password="root";
16.     public int baseUpdate(String sql,Object ... args){
17.         // 向 Emp表中增加一条数据
18.         Connection connection = null;
19.         PreparedStatement preparedStatement=null;
20.         int rows=0;
21.         try{
22.             Class.forName(driver);
23.             connection = DriverManager.getConnection(url, user,password);
24.             preparedStatement = connection.prepareStatement(sql);
25.             //设置参数
26.             for (int i = 0; i <args.length ; i++) {
27.                 preparedStatement.setObject(i+1, args[i]);
28.             }
29.             //执行CURD
30.             rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
31.         }catch (Exception e){
32.             e.printStackTrace();
33.         }finally {
34.             if(null != preparedStatement){
35.                 try {
36.                     preparedStatement.close();
37.                 } catch (SQLException e) {
38.                     e.printStackTrace();
39.                 }
40.             }
41.             if(null != connection){
42.                 try {
43.                     connection.close();
44.                 } catch (SQLException e) {
45.                     e.printStackTrace();
46.                 }
47.             }
48.         }
49.         return rows;
50.     }
51.     public List baseQuery(Class clazz,String sql,Object ... args) {
52.         // 查询名字中包含字母A的员工信息
53.         Connection connection = null;
54.         PreparedStatement preparedStatement=null;
55.         ResultSet resultSet=null;
56.         List list =null;
57.         try{
58.             Class.forName(driver);
59.             connection = DriverManager.getConnection(url, user,password);
60.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
61.             //设置参数
62.             for (int i = 0; i <args.length ; i++) {
63.                 preparedStatement.setObject(i+1, args[i]);
64.             }
65.             //执行CURD
66.             resultSet = preparedStatement.executeQuery();// 这里不需要再传入SQL语句
67.             list=new ArrayList() ;
68.             // 根据字节码获取所有 的属性
69.             Field[] fields = clazz.getDeclaredFields();
70.             for (Field field : fields) {
71.                 field.setAccessible(true);// 设置属性可以 访问
72.             }
73.             while(resultSet.next()){
74.                 // 通过反射创建对象
75.                 Object obj = clazz.newInstance();//默认在通过反射调用对象的空参构造方法
76.                 for (Field field : fields) {// 临时用Field设置属性
77.                     String fieldName = field.getName();// empno  ename job
    .... ...
78.                     Object data = resultSet.getObject(fieldName);
79.                     field.set(obj,data);
80.                 }
81.                 list.add(obj);
82.             }
83.         }catch (Exception e){
84.             e.printStackTrace();
85.         }finally {
86.             if(null != resultSet){
87.                 try {
88.                     resultSet.close();
89.                 } catch (SQLException e) {
90.                     e.printStackTrace();
91.                 }
92.             }
93.             if(null != preparedStatement){
94.                 try {
95.                     preparedStatement.close();
96.                 } catch (SQLException e) {
97.                     e.printStackTrace();
98.                 }
99.             }
100.             if(null != connection){
101.                 try {
102.                     connection.close();
103.                 } catch (SQLException e) {
104.                     e.printStackTrace();
105.                 }
106.             }
107.         }
108.         return list;
109.     }
110. }

 







到实现类代码 







1.  package com.msb.dao.impl;
2.  import com.msb.dao.BaseDao;
3.  import com.msb.dao.EmpDao;
4.  import com.msb.pojo.Emp;
5.  import java.sql.*;
6.  import java.util.ArrayList;
7.  import java.util.List;
8.  /**
9.   * @Author: Ma HaiYang
10.  * @Description: MircoMessage:Mark_7001
11.  */
12. public class EmpDaoImpl extends BaseDao implements EmpDao {
13.     @Override
14.     public int addEmp(Emp emp) {
15.         String sql="insert into emp values(DEFAULT ,?,?,?,?,?,?,?)";
16.         return baseUpdate(sql,
    emp.getEname(),emp.getJob(),emp.getMgr(),emp.getHiredate(),emp.getSal(),emp.
    etComm(),emp.getDeptno());
17.     }
18.     @Override
19.     public int deleteByEmpno(int empno) {
20.         String sql="delete from emp where empno =?";
21.         return baseUpdate(sql, empno);
22.     }
23.     @Override
24.     public List<Emp> findAll() {
25.         String sql ="select * from emp";
26.         return baseQuery(Emp.class, sql );
27.     }
28.     @Override
29.     public int updateEmp(Emp emp) {
30.         String sql="update emp set ename =? ,job=?, mgr =?,hiredate
    =?,sal=?,comm=?,deptno=? where empno =?";
31.         return baseUpdate(sql,
    emp.getEname(),emp.getJob(),emp.getMgr(),emp.getHiredate(),emp.getSal(),emp.
    etComm(),emp.getDeptno(),emp.getEmpno());
32.     }
33. }

 







1.  package com.msb.dao.impl;
2.  import com.msb.dao.BaseDao;
3.  import com.msb.dao.DeptDao;
4.  import com.msb.pojo.Dept;
5.  import com.msb.pojo.Emp;
6.  import java.sql.*;
7.  import java.util.ArrayList;
8.  import java.util.List;
9.  /**
10.  * @Author: Ma HaiYang
11.  * @Description: MircoMessage:Mark_7001
12.  */
13. public class DeptDaoImpl extends BaseDao implements DeptDao {
14.     @Override
15.     public List<Dept> findAll() {
16.         String sql="select * from dept";
17.         return  baseQuery(Dept.class, sql);
18.     }
19.     @Override
20.     public int addDept(Dept dept) {
21.         String sql="insert into dept values(?,?,?)";
22.         return baseUpdate(sql,
    dept.getDeptno(),dept.getDname(),dept.getLoc());
23.     }
24. }

 






------------------------------------------------------------

