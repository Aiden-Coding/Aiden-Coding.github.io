
# 21_Spring_日志框架和测试支持

spring5框架自带了通用的日志封装,也可以整合自己的日志 

 1)spring移除了 LOG4jConfigListener,官方建议使用log4j2 

 2)spring5整合log4j2 

导入log4j2依赖 




1.          <!--log4j2 依赖-->
2.          <!--<dependency>
3.              <groupId>org.apache.logging.log4j</groupId>
4.              <artifactId>log4j-core</artifactId>
5.              <version>2.14.0</version>
6.          </dependency>-->
7.          <!--slf4-impl 包含了log4j2 依赖-->
8.          <dependency>
9.              <groupId>org.apache.logging.log4j</groupId>
10.             <artifactId>log4j-slf4j-impl</artifactId>
11.             <version>2.14.0</version>
12.             <scope>test</scope>
13.         </dependency> 




在resources目录下准备log4j2.xml的配置文件 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <Configuration status="DEBUG">
3.      <Appenders>
4.          <Console name="Console" target="SYSTEM_OUT">
5.              <PatternLayout pattern="%d{YYYY-MM-dd HH:mm:ss} [%t] %-5p
    %c{1}:%L - %msg%n" />
6.          </Console>
7.      </Appenders>
8.      <Loggers>
9.          <Root level="debug">
10.             <AppenderRef ref="Console" />
11.         </Root>
12.     </Loggers>
13. </Configuration> 













spring5关于测试工具的支持 




整合junit4 

依赖的jar 




1.          <!--Junit4单元测试-->
2.          <dependency>
3.              <groupId>junit</groupId>
4.              <artifactId>junit</artifactId>
5.              <version>4.13.1</version>
6.              <scope>test</scope>
7.          </dependency>
8.          <!--spring test测试支持包-->
9.          <dependency>
10.             <groupId>org.springframework</groupId>
11.             <artifactId>spring-test</artifactId>
12.             <version>5.3.5</version>
13.             <scope>test</scope>
14.         </dependency>

 




测试代码编写方式 




1.  package com.msb.test;
2.  import com.msb.config.SpringConfig;
3.  import com.msb.service.AccountService;
4.  import org.junit.Test;
5.  import org.junit.runner.RunWith;
6.  import org.springframework.beans.factory.annotation.Autowired;
7.  import org.springframework.context.ApplicationContext;
8.  import
    org.springframework.context.annotation.AnnotationConfigApplicationContext;
9.  import org.springframework.context.support.ClassPathXmlApplicationContext;
10. import org.springframework.lang.Nullable;
11. import org.springframework.test.context.ContextConfiguration;
12. import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;
13. /**
14.  * @Author: Ma HaiYang
15.  * @Description: MircoMessage:Mark_7001
16.  */
17. @RunWith(SpringJUnit4ClassRunner.class)// 指定测试支持类
18. @ContextConfiguration("classpath:applicationContext.xml")// 指定核心配置文件位置
19. public class Test2 {
20.     @Autowired // 注入要获取的bean
21.     private  AccountService accountService;
22.     @Test()
23.     public void testTransaction(){
24.         int rows = accountService.transMoney(1, 2, 100);
25.         System.out.println(rows);
26.     }
27. }

 







整合junit5 




依赖的jar 




1.          <!--junit5单元测试-->
2.          <dependency>
3.              <groupId>org.junit.jupiter</groupId>
4.              <artifactId>junit-jupiter-api</artifactId>
5.              <version>5.7.0</version>
6.              <scope>test</scope>
7.          </dependency>

测试代码编写方式 




1.  package com.msb.test;
2.  import com.msb.service.AccountService;
3.  import org.junit.jupiter.api.Test;
4.  import org.junit.jupiter.api.extension.ExtendWith;
5.  import org.springframework.beans.factory.annotation.Autowired;
6.  import org.springframework.test.context.ContextConfiguration;
7.  import org.springframework.test.context.junit.jupiter.SpringExtension;
8.  import org.springframework.test.context.junit.jupiter.SpringJUnitConfig;
9.  /**
10.  * @Author: Ma HaiYang
11.  * @Description: MircoMessage:Mark_7001
12.  */
13. /*使用ExtentWith和ContextConfiguration注解*/
14. /*@ExtendWith(SpringExtension.class)
15. @ContextConfiguration("classpath:applicationContext.xml")*/
16. // 使用复合注解
17. @SpringJUnitConfig(locations = "classpath:applicationContext.xml")
18. public class Test3 {
19.     @Autowired // 注入要获取的bean
20.     private  AccountService accountService;
21.     @Test
22.     public void testTransaction(){
23.         int rows = accountService.transMoney(1, 2, 100);
24.         System.out.println(rows);
25.     }
26. }

 


















------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
