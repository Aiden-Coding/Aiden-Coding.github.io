
# 6_PrepareStatement完成CURD




1.  package com.msb.test3;
2.  import com.msb.entity.Emp;
3.  import java.sql.*;
4.  import java.util.ArrayList;
5.  import java.util.List;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. public class TestPreparedSstatement {
11.     private static String driver ="com.mysql.cj.jdbc.Driver";
12.     private static String
    url="jdbc:mysql://127.0.0.1:3306/mydb?useSSL=false&useUnicode=true&character
    ncoding=UTF-8&serverTimezone=Asia/Shanghai&allowPublicKeyRetrieval=true";
13.     private static String user="root";
14.     private static String password="root";
15.     public static void main(String[] args) {
16.         //testAdd();
17.         //testUpdate();
18.         //testDelete();
19.         testQuery();
20.     }
21.     public static void testAdd(){
22.         // 向 Emp表中增加一条数据
23.         Connection connection = null;
24.         PreparedStatement preparedStatement=null;
25.         try{
26.             Class.forName(driver);
27.             connection = DriverManager.getConnection(url, user,password);
28.             String sql="insert into emp values(DEFAULT ,?,?,?,?,?,?,?)";
29.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
30.             //设置参数
31.             preparedStatement.setString(1,"Mark");
32.             preparedStatement.setString(2,"MANAGER" );
33.             preparedStatement.setInt(3,7839);
34.             preparedStatement.setDate(4,new
    Date(System.currentTimeMillis()));
35.             preparedStatement.setDouble(5,3000.12);
36.             preparedStatement.setDouble(6,0.0);
37.             preparedStatement.setDouble(7,30);
38.             //执行CURD
39.             int rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
40.             System.out.println(rows);
41.         }catch (Exception e){
42.             e.printStackTrace();
43.         }finally {
44.             if(null != preparedStatement){
45.                 try {
46.                     preparedStatement.close();
47.                 } catch (SQLException e) {
48.                     e.printStackTrace();
49.                 }
50.             }
51.             if(null != connection){
52.                 try {
53.                     connection.close();
54.                 } catch (SQLException e) {
55.                     e.printStackTrace();
56.                 }
57.             }
58.         }
59.     }
60.     public static void testUpdate(){
61.         // 根据工号修改员工表中的数据
62.         Connection connection = null;
63.         PreparedStatement preparedStatement=null;
64.         try{
65.             Class.forName(driver);
66.             connection = DriverManager.getConnection(url, user,password);
67.             String sql="update emp set ename =? ,job=? where empno =?";
68.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
69.             //设置参数
70.             preparedStatement.setString(1,"Jhon");
71.             preparedStatement.setString(2,"ANALYST" );
72.             preparedStatement.setInt(3,7935);
73.             //执行CURD
74.             int rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
75.             System.out.println(rows);
76.         }catch (Exception e){
77.             e.printStackTrace();
78.         }finally {
79.             if(null != preparedStatement){
80.                 try {
81.                     preparedStatement.close();
82.                 } catch (SQLException e) {
83.                     e.printStackTrace();
84.                 }
85.             }
86.             if(null != connection){
87.                 try {
88.                     connection.close();
89.                 } catch (SQLException e) {
90.                     e.printStackTrace();
91.                 }
92.             }
93.         }
94.     }
95.     public static void testDelete(){
96.         // 根据工号删除员工表中的数据
97.         Connection connection = null;
98.         PreparedStatement preparedStatement=null;
99.         try{
100.             Class.forName(driver);
101.             connection = DriverManager.getConnection(url, user,password);
102.             String sql="delete from emp where empno =?";
103.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
104.             //设置参数
105.             preparedStatement.setInt(1,7935);
106.             //执行CURD
107.             int rows =preparedStatement.executeUpdate();// 这里不需要再传入SQL语句
108.             System.out.println(rows);
109.         }catch (Exception e){
110.             e.printStackTrace();
111.         }finally {
112.             if(null != preparedStatement){
113.                 try {
114.                     preparedStatement.close();
115.                 } catch (SQLException e) {
116.                     e.printStackTrace();
117.                 }
118.             }
119.             if(null != connection){
120.                 try {
121.                     connection.close();
122.                 } catch (SQLException e) {
123.                     e.printStackTrace();
124.                 }
125.             }
126.         }
127.     }
128.     public static void testQuery(){
129.         // 查询名字中包含字母A的员工信息
130.         Connection connection = null;
131.         PreparedStatement preparedStatement=null;
132.         ResultSet resultSet=null;
133.         List<Emp> list =null;
134.         try{
135.             Class.forName(driver);
136.             connection = DriverManager.getConnection(url, user,password);
137.             /*
138.              * 1使用PreparedStatement语句对象防止注入攻击
139.              * 2PreparedStatement 可以使用 ? 作为参数的占位符
140.              * 3使用?作为占位符,即使是字符串和日期类型,也不使用单独再添加 ''
141.              * 4connection.createStatement();获得的是普通语句对象 Statement
142.              \*
    5connection.prepareStatement(sql);可以获得一个预编译语句对象PreparedStatement
143.              * 6如果SQL语句中有?作为参数占位符号,那么要在执行CURD之前先设置参数
144.              * 7通过set***(问号的编号,数据) 方法设置参数
145.              * */
146.             String sql="select * from emp where ename like ? ";
147.             preparedStatement =
    connection.prepareStatement(sql);//这里已经传入SQL语句
148.             //设置参数
149.             preparedStatement.setString(1,"%A%");
150.             //执行CURD
151.             resultSet = preparedStatement.executeQuery();// 这里不需要再传入SQL语句
152.             list=new ArrayList<Emp>() ;
153.             while(resultSet.next()){
154.                 int empno = resultSet.getInt("empno");
155.                 String ename = resultSet.getString("ename");
156.                 String job = resultSet.getString("job");
157.                 int mgr = resultSet.getInt("mgr");
158.                 Date hiredate = resultSet.getDate("hiredate");
159.                 double sal= resultSet.getDouble("sal");
160.                 double comm= resultSet.getDouble("comm");
161.                 int deptno= resultSet.getInt("deptno");
162.                 Emp emp =new Emp(empno, ename, job, mgr, hiredate, sal,
    comm, deptno);
163.                 list.add(emp);
164.             }
165.         }catch (Exception e){
166.             e.printStackTrace();
167.         }finally {
168.             if(null != resultSet){
169.                 try {
170.                     resultSet.close();
171.                 } catch (SQLException e) {
172.                     e.printStackTrace();
173.                 }
174.             }
175.             if(null != preparedStatement){
176.                 try {
177.                     preparedStatement.close();
178.                 } catch (SQLException e) {
179.                     e.printStackTrace();
180.                 }
181.             }
182.             if(null != connection){
183.                 try {
184.                     connection.close();
185.                 } catch (SQLException e) {
186.                     e.printStackTrace();
187.                 }
188.             }
189.         }
190.         // 遍历集合
191.         for (Emp emp : list) {
192.             System.out.println(emp);
193.         }
194.     }
195. }






------------------------------------------------------------

