
# 10_DAO模式

DAO(Data Access Object)是一个数据访问接口，数据访问：顾名思义就是与数据库打交道。夹在
[业务逻辑](https://baike.baidu.com/item/%E4%B8%9A%E5%8A%A1%E9%80%BB%E8%BE%91)与数据库资源中间。
在核心[J2EE](https://baike.baidu.com/item/J2EE)模式中是这样介绍DAO模式的：为了建立一个健壮的J2EE应用，应该将所有对
[数据源](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E6%BA%90)的访问操作抽象封装在一个公共
[API](https://baike.baidu.com/item/API/10154)中。用程序设计的语言来说，就是建立一个接口，接口中定义了此应用程序中将会用到的所有
[事务](https://baike.baidu.com/item/%E4%BA%8B%E5%8A%A1)方法。在这个应用程序中，当需要和数据源进行交互的时候则使用这个接口，并且编写一个单独的类来实现这个接口在逻辑上对应这个特定的数据存储
. 

简单来说,就是定义一个接口,规定一些增删改查的方法,然后交给实现类去实现, 它介于数据库和业务逻辑代码之间,这样当我们需要操作数据库是,根据接口定义的API去操作数据库就可以了
,每个方法都是一个原子性的操作,例如：增加、修改、删除等 

Dao模式要求项目必须具备这样几个结构 

1实体类:和数据库表格一一对应的类,单独放入一个包中,包名往往是 pojo/entity/bean,要操作的每个表格都应该有对应的实体类 

emp > class Emp   

dept > class Dept   

account > class Account  

2DAO 层:定义了对数据要执行那些操作的接口和实现类,包名往往是 dao/mapper,要操作的每个表格都应该有对应的接口和实现类 

emp > interface EmpDao >EmpDaoImpl 

dept > interface DeptDao> DeptDaoImpl 

3Mybatis/Spring JDBCTemplate 中,对DAO层代码进行了封装,代码编写方式会有其他变化 




  

### 项目的搭建 

1.创建项目 

2.添加jar包 

3.创建包 

4.创建实体类Emp 

5.创建后台的接口EmpDao和实现类EmpDaoImpl 

导入各个层级的接口和页面之后的项目 




项目结构截图如下 


![image](data:image/png;base64,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)






实体类代码 




1.  public class Emp implements Serializable {
2.      private Integer empno;
3.      private String ename;
4.      private String job;
5.      private Integer mgr;
6.      private Date hiredate;
7.      private Double sal;
8.      private Double comm;
9.      private Integer deptno; 




1.  public class Dept implements Serializable {
2.      private Integer deptno;
3.      private String dname;
4.      private String loc; 




DAO接口代码 




1.  package com.msb.dao;
2.  import com.msb.pojo.Emp;
3.  /**
4.   * @Author: Ma HaiYang
5.   * @Description: MircoMessage:Mark_7001
6.   */
7.  public interface EmpDao {
8.      /**
9.       * 向数据库Emp表中增加一条数据的方法
10.      * @param emp 要增加的数据封装成的Emp类的对象
11.      * @return 增加成功返回大于0 的整数,增加失败返回0
12.      */
13.     int addEmp(Emp emp);
14.     /**
15.      * 根据员工编号删除员工信息的方法
16.      * @param empno 要删除的员工编号
17.      * @return 删除成功返回大于0的整数,失败返回0
18.      */
19.     int deleteByEmpno(int empno);
20. }

 

DAO实现类代码 




1.  package com.msb.dao.impl;
2.  import com.msb.dao.EmpDao;
3.  import com.msb.pojo.Emp;
4.  import java.sql.*;
5.  /**
6.   * @Author: Ma HaiYang
7.   * @Description: MircoMessage:Mark_7001
8.   */
9.  public class EmpDaoImpl implements EmpDao {
10.     private static String driver ="com.mysql.cj.jdbc.Driver";
11.     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
12.     private static String user="root";
13.     private static String password="root";
14.     @Override
15.     public int addEmp(Emp emp) {
16.         // 向 Emp表中增加一条数据
17.         Connection connection = null;
18.         PreparedStatement preparedStatement=null;
19.         int rows=0;
20.         try{
21.             Class.forName(driver);
22.             connection = DriverManager.getConnection(url, user,password);
23.             String sql="insert into emp values(DEFAULT ,?,?,?,?,?,?,?)";
24.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
25.             //设置参数
26.             preparedStatement.setObject(1,emp.getEname());
27.             preparedStatement.setObject(2,emp.getJob() );
28.             preparedStatement.setObject(3,emp.getMgr());
29.             preparedStatement.setObject(4,emp.getHiredate());
30.             preparedStatement.setObject(5,emp.getSal());
31.             preparedStatement.setObject(6,emp.getComm());
32.             preparedStatement.setObject(7,emp.getDeptno());
33.             //执行CURD
34.             rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
35.         }catch (Exception e){
36.             e.printStackTrace();
37.         }finally {
38.             if(null != preparedStatement){
39.                 try {
40.                     preparedStatement.close();
41.                 } catch (SQLException e) {
42.                     e.printStackTrace();
43.                 }
44.             }
45.             if(null != connection){
46.                 try {
47.                     connection.close();
48.                 } catch (SQLException e) {
49.                     e.printStackTrace();
50.                 }
51.             }
52.         }
53.         return rows;
54.     }
55.     @Override
56.     public int deleteByEmpno(int empno) {
57.         // 向 Emp表中增加一条数据
58.         Connection connection = null;
59.         PreparedStatement preparedStatement=null;
60.         int rows=0;
61.         try{
62.             Class.forName(driver);
63.             connection = DriverManager.getConnection(url, user,password);
64.             String sql="delete from emp where empno =?";
65.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
66.             //设置参数
67.             preparedStatement.setObject(1,empno);
68.             //执行CURD
69.             rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
70.         }catch (Exception e){
71.             e.printStackTrace();
72.         }finally {
73.             if(null != preparedStatement){
74.                 try {
75.                     preparedStatement.close();
76.                 } catch (SQLException e) {
77.                     e.printStackTrace();
78.                 }
79.             }
80.             if(null != connection){
81.                 try {
82.                     connection.close();
83.                 } catch (SQLException e) {
84.                     e.printStackTrace();
85.                 }
86.             }
87.         }
88.         return rows;
89.     }
90. }

 






------------------------------------------------------------

