
# 20_Spring_零XML事务控制

创建配置类 




1.  package com.msb.config;
2.  import com.alibaba.druid.pool.DruidDataSource;
3.  import org.springframework.beans.factory.annotation.Value;
4.  import org.springframework.context.annotation.Bean;
5.  import org.springframework.context.annotation.ComponentScan;
6.  import org.springframework.context.annotation.Configuration;
7.  import org.springframework.context.annotation.PropertySource;
8.  import org.springframework.jdbc.core.JdbcTemplate;
9.  import org.springframework.jdbc.datasource.DataSourceTransactionManager;
10. import org.springframework.transaction.PlatformTransactionManager;
11. import
    org.springframework.transaction.annotation.EnableTransactionManagement;
12. import javax.sql.DataSource;
13. /**
14.  * @Author: Ma HaiYang
15.  * @Description: MircoMessage:Mark_7001
16.  */
17. @Configuration  // 配置类标志注解
18. @ComponentScan(basePackages = "com.msb") // spring包扫描
19. @PropertySource("classpath:jdbc.properties") // 读取属性配置文件
20. @EnableTransactionManagement // 开启事务注解
21. public class SpringConfig {
22.     @Value("${jdbc_driver}")
23.     private String driver;
24.     @Value("${jdbc_url}")
25.     private String url;
26.     @Value("${jdbc_username}")
27.     private String username;
28.     @Value("${jdbc_password}")
29.     private String password;
30.     /*创建数据库连接池*/
31.     @Bean
32.     public DruidDataSource getDruidDataSource(){
33.         DruidDataSource dataSource=new DruidDataSource();
34.         dataSource.setDriverClassName(driver);
35.         dataSource.setUrl(url);
36.         dataSource.setUsername(username);
37.         dataSource.setPassword(password);
38.         return dataSource;
39.     }
40.     /*创建JdbcTemplate对象*/
41.     @Bean
42.     public JdbcTemplate getJdbcTemplate(DataSource dataSource){
43.         JdbcTemplate jdbcTemplate=new JdbcTemplate();
44.         jdbcTemplate.setDataSource(dataSource);
45.         return jdbcTemplate;
46.     }
47.     /*创建事务管理器*/
48.     @Bean
49.     public PlatformTransactionManager
    getPlatformTransactionManager(DataSource dataSource){
50.         DataSourceTransactionManager transactionManager =new
    DataSourceTransactionManager();
51.         transactionManager.setDataSource(dataSource);
52.         return transactionManager;
53.     }
54. }

 




测试代码 




1.  @Test()
2.      public void testTransaction3(){
3.          ApplicationContext context =new
    AnnotationConfigApplicationContext(SpringConfig.class);
4.          AccountService accountService =
    context.getBean(AccountService.class);
5.          int rows = accountService.transMoney(1, 2, 100);
6.          System.out.println(rows);
7.      } 

















































































------------------------------------------------------------

