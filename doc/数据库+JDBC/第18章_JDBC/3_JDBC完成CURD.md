
# 3_JDBC完成CURD

### 删除和修改部门信息 

### 


1.  ### package com.msb.test1;
2.  ### import java.sql.Connection;
3.  ### import java.sql.DriverManager;
4.  ### import java.sql.SQLException;
5.  ### import java.sql.Statement;
6.  ### /**
7.  ###  * @Author: Ma HaiYang
8.  ###  * @Description: MircoMessage:Mark_7001
9.  ###  */
10. ### public class TestJDBC4 {
11. ###     private static String driver ="com.mysql.cj.jdbc.Driver";
12. ###     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
13. ###     private static String user="root";
14. ###     private static String password="root";
15. ###     public static void main(String[] args)  {
16. ###         //testDelete();
17. ###         testUpdate();
18. ###     }
19. ###     public static void testUpdate(){
20. ###         Connection connection=null;
21. ###         Statement statement=null;
22. ###         try{
23. ###             Class.forName(driver);
24. ###             connection =DriverManager.getConnection(url, user,password);
25. ###             statement = connection.createStatement();
26. ###             String sql="update dept set dname='总部',loc='北京' where deptno=
    30 ";
27. ###             int rows = statement.executeUpdate(sql);
28. ###             System.out.println("影响数据行数为:"+rows);
29. ###         }catch (Exception e){
30. ###             e.printStackTrace();
31. ###         }finally {
32. ###             if(null != statement){
33. ###                 try {
34. ###                     statement.close();
35. ###                 } catch (SQLException e) {
36. ###                     e.printStackTrace();
37. ###                 }
38. ###             }
39. ###             if(null != connection){
40. ###                 try {
41. ###                     connection.close();
42. ###                 } catch (SQLException e) {
43. ###                     e.printStackTrace();
44. ###                 }
45. ###             }
46. ###         }
47. ###     }
48. ###     public static void testDelete(){
49. ###         Connection connection=null;
50. ###         Statement statement=null;
51. ###         try{
52. ###             Class.forName(driver);
53. ###             connection =DriverManager.getConnection(url, user,password);
54. ###             statement = connection.createStatement();
55. ###             String sql="delete from dept where deptno =40";
56. ###             int rows = statement.executeUpdate(sql);
57. ###             System.out.println("影响数据行数为:"+rows);
58. ###         }catch (Exception e){
59. ###             e.printStackTrace();
60. ###         }finally {
61. ###             if(null != statement){
62. ###                 try {
63. ###                     statement.close();
64. ###                 } catch (SQLException e) {
65. ###                     e.printStackTrace();
66. ###                 }
67. ###             }
68. ###             if(null != connection){
69. ###                 try {
70. ###                     connection.close();
71. ###                 } catch (SQLException e) {
72. ###                     e.printStackTrace();
73. ###                 }
74. ###             }
75. ###         }
76. ###     }
77. ### }

** **

### 


### 


### 


### 


### 需求:查询全部 员工信息 

### 


1.  ### package com.msb.test1;
2.  ### import java.sql.*;
3.  ### /**
4.  ###  * @Author: Ma HaiYang
5.  ###  * @Description: MircoMessage:Mark_7001
6.  ###  */
7.  ### public class TestJDBC5 {
8.  ###     private static String driver ="com.mysql.cj.jdbc.Driver";
9.  ###     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
10. ###     private static String user="root";
11. ###     private static String password="root";
12. ###     public static void main(String[] args)  {
13. ###         testQuery();
14. ###     }
15. ###     public static void testQuery(){
16. ###         Connection connection = null;
17. ###         Statement statement=null;
18. ###         ResultSet resultSet=null;
19. ###         try{
20. ###             Class.forName(driver);
21. ###             connection = DriverManager.getConnection(url, user,password);
22. ###             statement = connection.createStatement();
23. ###             String sql="select * from emp";
24. ###             resultSet = statement.executeQuery(sql);
25. ###             while(resultSet.next()){
26. ###                 int empno = resultSet.getInt("empno");
27. ###                 String ename = resultSet.getString("ename");
28. ###                 String job = resultSet.getString("job");
29. ###                 int mgr = resultSet.getInt("mgr");
30. ###                 Date hiredate = resultSet.getDate("hiredate");
31. ###                 double sal= resultSet.getDouble("sal");
32. ###                 double comm= resultSet.getDouble("comm");
33. ###                 int deptno= resultSet.getInt("deptno");
34. ###                 System.out.println(""+empno+" "+ename+" "+job+" "+mgr+"
    "+hiredate+" "+sal+" "+comm+" "+deptno);
35. ###             }
36. ###         }catch (Exception e){
37. ###             e.printStackTrace();
38. ###         }finally {
39. ###             if(null != resultSet){
40. ###                 try {
41. ###                     resultSet.close();
42. ###                 } catch (SQLException e) {e.printStackTrace();
43. ###                 }
44. ###             }
45. ###             if(null != statement){
46. ###                 try {
47. ###                     statement.close();
48. ###                 } catch (SQLException e) {
49. ###                     e.printStackTrace();
50. ###                 }
51. ###             }
52. ###             if(null != connection){
53. ###                 try {
54. ###                     connection.close();
55. ###                 } catch (SQLException e) {
56. ###                     e.printStackTrace();
57. ###                 }
58. ###             }
59. ###         }
60. ###     }
61. ### }

** **

### 


•       ResultSet里的数据一行一行排列，每行有多个字段，且有一个记录指针，指针所指的数据行叫做当前数据行，我们只能来操作当前的数据行。我们如果想要取得某一条记录，就要使用
ResultSet的next()方法 ,如果我们想要得到ResultSet里的所有记录，就应该使用while循环。 

•       ResultSet对象自动维护指向当前数据行的游标。每调用一次next()方法，游标向下移动一行。 

•       初始状态下记录指针指向第一条记录的前面，通过next()方法指向第一条记录。循环完毕后指向最后一条记录的后面。 

                                          


|                                       |方法名                                    |                            |说    明                      |
|---------------------------------------|----------------------------|
|                                       |boolean   next()                       |                            |将光标从当前位置向下移动一行              |
|                                       |boolean   previous()                   |                            |游标从当前位置向上移动一行               |
|                                       |void   close()                         |                            |关闭ResultSet 对象              |
|                                       |int   getInt(int colIndex)             |                            |以int形式获取结果集当前行指定列号值         |
|                                       |int   getInt(String colLabel)          |                            |以int形式获取结果集当前行指定列名值         |
|                                       |float   getFloat(int colIndex)         |                            |以float形式获取结果集当前行指定列号值       |
|                                       |Float   getFloat(String colLabel)      |                            |以float形式获取结果集当前行指定列名值       |
|                                       |String   getString(int colIndex)       |                            |以String 形式获取结果集当前行指定列号值     |
|                                       |StringgetString(String   colLabel)     |                            |以String形式获取结果集当前行指定列名值      |

  

       作为一种好的编程风格，应在不需要Statement对象和Connection对象时显式地关闭它们。关闭Statement对象和Connection
对象的语法形式为：用户不必关闭ResultSet。当它的 Statement 关闭、重新执行或用于从多结果序列中获取下一个结果时，该ResultSet将被自动关闭。
**为什么将结果封装成对象或者对象集合?** 

1java是面向对象的编程语言,java中所有的数据处理都是基于面向对象的编码风格实现的,让数据以符合java风格的形式存在,便于对数据的后续处理 

2ResultSet 集合虽然可以存放数据,但是它是JDBC中查询数据的一种手段,是一种数据的临时存储方案,使用完毕是要进行释放和关闭 

  

#### 封装后台查询数据并在前台显示 


![image](data:image/jpg;base64,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)
如何将结果集中的数据在java中进行存储和传递? 

准备和数据库表格相对应的一个实体类,用于封装结果集中的每一条数据,数据库表格中的每一个字段就是实体类的一个属性,实体类的一个对象就可以用于存储数据库表中的一条记录
. 

准备实体类 




1.  package com.msb.entity;
2.  import java.io.Serializable;
3.  import java.util.Date;
4.  /**
5.   * @Author: Ma HaiYang
6.   * @Description: MircoMessage:Mark_7001
7.   */
8.  /*
9.  * 实体类:
10. * 和数据库表格名称和字段是一一对应的类
11. * 该类的对象主要用处是存储从数据库中查询出来的数据
12. * 除此之外,该类没有任何的其他功能
13. * 要求
14. * 1类名和表名保持一致  (见名知意)
15. * 2属性个数和数据库的表的列数保持一致
16. * 3属性的数据类型和列的数据类型保持一致
17. * 4属性名和数据库表格的列名要保持一致
18. * 5所有的属性必须都是私有的 (出于安全考虑)
19. * 6实体类的属性推荐写成包装类
20. * 7日期类型推荐写成java.util.Date
21. * 8所有的属性都要有get和set方法
22. * 9必须具备空参构造方法
23. * 10实体类应当实现序列化接口 (mybatis缓存  分布式需要 )
24. * 11实体类中其他构造方法可选
25. * */
26. public class Emp implements Serializable {
27.     private Integer empno;
28.     private String ename;
29.     private String job;
30.     private Integer mgr;
31.     private Date hiredate;
32.     private Double sal;
33.     private Double comm;
34.     private Integer deptno;
35.     @Override
36.     public String toString() {
37.         return "Emp{" +
38.                 "empno=" + empno +
39.                 ", ename='" + ename + '\'' +
40.                 ", job='" + job + '\'' +
41.                 ", mgr=" + mgr +
42.                 ", hiredate=" + hiredate +
43.                 ", sal=" + sal +
44.                 ", comm=" + comm +
45.                 ", deptno=" + deptno +
46.                 '}';
47.     }
48.     public Emp(Integer empno, String ename, String job, Integer mgr, Date
    hiredate, Double sal, Double comm, Integer deptno) {
49.         this.empno = empno;
50.         this.ename = ename;
51.         this.job = job;
52.         this.mgr = mgr;
53.         this.hiredate = hiredate;
54.         this.sal = sal;
55.         this.comm = comm;
56.         this.deptno = deptno;
57.     }
58.     public Emp(){
59.     }
60.     public Integer getEmpno() {
61.         return empno;
62.     }
63.     public void setEmpno(Integer empno) {
64.         this.empno = empno;
65.     }
66.     public String getEname() {
67.         return ename;
68.     }
69.     public void setEname(String ename) {
70.         this.ename = ename;
71.     }
72.     public String getJob() {
73.         return job;
74.     }
75.     public void setJob(String job) {
76.         this.job = job;
77.     }
78.     public Integer getMgr() {
79.         return mgr;
80.     }
81.     public void setMgr(Integer mgr) {
82.         this.mgr = mgr;
83.     }
84.     public Date getHiredate() {
85.         return hiredate;
86.     }
87.     public void setHiredate(Date hiredate) {
88.         this.hiredate = hiredate;
89.     }
90.     public Double getSal() {
91.         return sal;
92.     }
93.     public void setSal(Double sal) {
94.         this.sal = sal;
95.     }
96.     public Double getComm() {
97.         return comm;
98.     }
99.     public void setComm(Double comm) {
100.         this.comm = comm;
101.     }
102.     public Integer getDeptno() {
103.         return deptno;
104.     }
105.     public void setDeptno(Integer deptno) {
106.         this.deptno = deptno;
107.     }
108. }

 

使用实体类封装结果集 




1.  package com.msb.test1;
2.  import com.msb.entity.Emp;
3.  import java.sql.*;
4.  import java.util.ArrayList;
5.  import java.util.List;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. public class TestJDBC5 {
11.     private static String driver ="com.mysql.cj.jdbc.Driver";
12.     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
13.     private static String user="root";
14.     private static String password="root";
15.     public static void main(String[] args)  {
16.         List<Emp> emps = testQuery();
17.         // 遍历集合
18.         for (Emp emp : emps) {
19.             System.out.println(emp);
20.         }
21.     }
22.     public  static List<Emp>  testQuery(){
23.         Connection connection = null;
24.         Statement statement=null;
25.         ResultSet resultSet=null;
26.         List<Emp> list =null;
27.         try{
28.             Class.forName(driver);
29.             connection = DriverManager.getConnection(url, user,password);
30.             statement = connection.createStatement();
31.             String sql="select * from emp";
32.             resultSet = statement.executeQuery(sql);
33.             list=new ArrayList<>();
34.             while(resultSet.next()){
35.                 int empno = resultSet.getInt("empno");
36.                 String ename = resultSet.getString("ename");
37.                 String job = resultSet.getString("job");
38.                 int mgr = resultSet.getInt("mgr");
39.                 Date hiredate = resultSet.getDate("hiredate");
40.                 double sal= resultSet.getDouble("sal");
41.                 double comm= resultSet.getDouble("comm");
42.                 int deptno= resultSet.getInt("deptno");
43.                 Emp emp =new Emp(empno, ename, job, mgr, hiredate, sal,
    comm, deptno);
44.                 list.add(emp);
45.             }
46.         }catch (Exception e){
47.             e.printStackTrace();
48.         }finally {
49.             if(null != resultSet){
50.                 try {
51.                     resultSet.close();
52.                 } catch (SQLException e) {e.printStackTrace();
53.                 }
54.             }
55.             if(null != statement){
56.                 try {
57.                     statement.close();
58.                 } catch (SQLException e) {
59.                     e.printStackTrace();
60.                 }
61.             }
62.             if(null != connection){
63.                 try {
64.                     connection.close();
65.                 } catch (SQLException e) {
66.                     e.printStackTrace();
67.                 }
68.             }
69.         }
70.         return list;
71.     }
72. }

 




   



------------------------------------------------------------

