
# 15_Spring_JDBCTemplate批操作

一次连接,操作表格里的多条数据,就是批量操作 




1 批量增加 

2 批量修改 

3 批量删除 




实体类 




1.  package com.msb.pojo;
2.  import lombok.AllArgsConstructor;
3.  import lombok.Data;
4.  import lombok.NoArgsConstructor;
5.  import java.io.Serializable;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. @AllArgsConstructor
11. @NoArgsConstructor
12. @Data
13. public class Dept implements Serializable {
14.     private Integer deptno;
15.     private String dname;
16.     private String loc;
17. }

 




DeptService 




1.  package com.msb.service;
2.  import com.msb.pojo.Dept;
3.  import java.util.List;
4.  /**
5.   * @Author: Ma HaiYang
6.   * @Description: MircoMessage:Mark_7001
7.   */
8.  public interface DeptService {
9.      int[] deptBatchAdd(List<Dept> depts);
10.     int[] deptBatchUpdate(List<Dept> depts);
11.     int[] deptBatchDelete(List<Integer> deptnos);
12. }

 







1.  package com.msb.service.impl;
2.  import com.msb.dao.DeptDao;
3.  import com.msb.pojo.Dept;
4.  import com.msb.service.DeptService;
5.  import org.springframework.beans.factory.annotation.Autowired;
6.  import org.springframework.stereotype.Service;
7.  import java.util.List;
8.  /**
9.   * @Author: Ma HaiYang
10.  * @Description: MircoMessage:Mark_7001
11.  */
12. @Service
13. public class DeptServiceImpl implements DeptService {
14.     @Autowired
15.     private DeptDao deptDao;
16.     @Override
17.     public int[] deptBatchAdd(List<Dept> depts) {
18.         return deptDao.deptBatchAdd(depts);
19.     }
20.     @Override
21.     public int[] deptBatchUpdate(List<Dept> depts) {
22.         return  deptDao.deptBatchUpdate(depts);
23.     }
24.     @Override
25.     public int[] deptBatchDelete(List<Integer> deptnos) {
26.         return  deptDao.deptBatchDelete(deptnos);
27.     }
28. }

 







DeptDao  







1.  package com.msb.dao;
2.  import com.msb.pojo.Dept;
3.  import java.util.List;
4.  /**
5.   * @Author: Ma HaiYang
6.   * @Description: MircoMessage:Mark_7001
7.   */
8.  public interface DeptDao {
9.      int[] deptBatchAdd(List<Dept> depts);
10.     int[] deptBatchUpdate(List<Dept> depts);
11.     int[] deptBatchDelete(List<Integer> deptnos);
12. }

 










1.  package com.msb.dao.impl;
2.  import com.msb.dao.DeptDao;
3.  import com.msb.pojo.Dept;
4.  import org.springframework.beans.factory.annotation.Autowired;
5.  import org.springframework.jdbc.core.JdbcTemplate;
6.  import org.springframework.stereotype.Repository;
7.  import java.util.LinkedList;
8.  import java.util.List;
9.  /**
10.  * @Author: Ma HaiYang
11.  * @Description: MircoMessage:Mark_7001
12.  */
13. @Repository
14. public class DeptDaoImpl implements DeptDao {
15.     @Autowired
16.     private JdbcTemplate jdbcTemplate;
17.     @Override
18.     public int[] deptBatchAdd(List<Dept> depts) {
19.         String sql ="insert into dept values(DEFAULT,?,?)";
20.         List<Object[]> args =new LinkedList<>();
21.         for (Dept dept : depts) {
22.             Object[] arg ={dept.getDname(),dept.getLoc()};
23.             args.add(arg);
24.         }
25.         return jdbcTemplate.batchUpdate(sql, args);
26.     }
27.     @Override
28.     public int[] deptBatchUpdate(List<Dept> depts) {
29.         String sql ="update dept set dname =? ,loc =? where deptno=?";
30.         List<Object[]> args =new LinkedList<>();
31.         for (Dept dept : depts) {
32.             Object[] arg ={dept.getDname(),dept.getLoc(),dept.getDeptno()};
33.             args.add(arg);
34.         }
35.         return jdbcTemplate.batchUpdate(sql, args);
36.     }
37.     @Override
38.     public int[] deptBatchDelete(List<Integer> deptnos) {
39.         String sql ="delete from dept where deptno =?";
40.         List<Object[]> args =new LinkedList<>();
41.         for (Integer deptno : deptnos) {
42.             Object[] arg ={deptno};
43.             args.add(arg);
44.         }
45.         return jdbcTemplate.batchUpdate(sql, args);
46.     }
47. }

 




测试 







1.  package com.msb.test;
2.  import com.msb.pojo.Dept;
3.  import com.msb.service.DeptService;
4.  import com.msb.service.EmpService;
5.  import org.junit.Test;
6.  import org.springframework.context.ApplicationContext;
7.  import org.springframework.context.support.ClassPathXmlApplicationContext;
8.  import java.util.ArrayList;
9.  import java.util.Arrays;
10. import java.util.List;
11. /**
12.  * @Author: Ma HaiYang
13.  * @Description: MircoMessage:Mark_7001
14.  */
15. public class Test2 {
16.     @Test
17.     public void testBatchAdd(){
18.         ApplicationContext context=new
    ClassPathXmlApplicationContext("applicationContext.xml");
19.         DeptService deptService = context.getBean(DeptService.class);
20.         List<Dept> depts =new ArrayList<>();
21.         for (int i = 0; i < 10; i++) {
22.             depts.add(new Dept(null,"name"+i,"loc"+i));
23.         }
24.         int[] ints = deptService.deptBatchAdd(depts);
25.         System.out.println(Arrays.toString(ints));
26.     }
27.     @Test
28.     public void testBatchUpdate(){
29.         ApplicationContext context=new
    ClassPathXmlApplicationContext("applicationContext.xml");
30.         DeptService deptService = context.getBean(DeptService.class);
31.         List<Dept> depts =new ArrayList<>();
32.         for (int i = 51; i <=60; i++) {
33.             depts.add(new Dept(i,"newname","newLoc"));
34.         }
35.         int[] ints = deptService.deptBatchUpdate(depts);
36.         System.out.println(Arrays.toString(ints));
37.     }
38.     @Test
39.     public void testBatchDelete(){
40.         ApplicationContext context=new
    ClassPathXmlApplicationContext("applicationContext.xml");
41.         DeptService deptService = context.getBean(DeptService.class);
42.         List<Integer> deptnos =new ArrayList<>();
43.         for (int i = 51; i <=69; i++) {
44.             deptnos.add(i);
45.         }
46.         int[] ints = deptService.deptBatchDelete(deptnos);
47.         System.out.println(Arrays.toString(ints));
48.     }
49. }

 


























































  












------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
