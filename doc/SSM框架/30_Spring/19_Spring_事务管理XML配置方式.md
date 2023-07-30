
# 19_Spring_事务管理XML配置方式

applicationContext中,通过AOP实现事务的控制 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <beans xmlns="http://www.springframework.org/schema/beans"
3.         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
4.         xmlns:p="http://www.springframework.org/schema/p"
5.         xmlns:c="http://www.springframework.org/schema/c"
6.         xmlns:util="http://www.springframework.org/schema/util"
7.         xmlns:context="http://www.springframework.org/schema/context"
8.         xmlns:aop="http://www.springframework.org/schema/aop"
9.         xmlns:tx="http://www.springframework.org/schema/tx"
10.        xsi:schemaLocation="
11.        http://www.springframework.org/schema/beans
12.        http://www.springframework.org/schema/beans/spring-beans.xsd
13.        http://www.springframework.org/schema/util
14.        http://www.springframework.org/schema/util/spring-util.xsd
15.        http://www.springframework.org/schema/context
16.        http://www.springframework.org/schema/context/spring-context.xsd
17.        http://www.springframework.org/schema/aop
18.        http://www.springframework.org/schema/aop/spring-aop.xsd
19.        http://www.springframework.org/schema/tx
20.        http://www.springframework.org/schema/tx/spring-tx.xsd
21. ">
22.     <context:component-scan base-package="com.msb"/>
23.     <!--读取jdbc配置文件-->
24.     <context:property-placeholder location="classpath:jdbc.properties"/>
25.     <!--配置德鲁伊连接池-->
26.     <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
27.         <property name="username" value="${jdbc_username}"></property>
28.         <property name="password" value="${jdbc_password}"></property>
29.         <property name="url" value="${jdbc_url}"></property>
30.         <property name="driverClassName" value="${jdbc_driver}"></property>
31.     </bean>
32.     <!--配置JDBCTemplate对象,并向里面注入DataSource-->
33.     <bean id="jdbcTemplate"
    class="org.springframework.jdbc.core.JdbcTemplate">
34.         <!--通过set方法注入连接池-->
35.         <property name="dataSource" ref="dataSource"></property>
36.     </bean>
37.     <!--配置一个事务管理器-->
38.     <bean id="transactionManager"
    class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
39.         <!--将数据源注入事务管理器-->
40.         <property name="dataSource"  ref="dataSource"></property>
41.     </bean>
42.     <!--配置通知-->
43.     <tx:advice id="txAdvice">
44.             <!--配置事务参数-->
45.             <tx:attributes>
46.                 <tx:method name="transMoney" isolation="DEFAULT"
    propagation="REQUIRED"/>
47.             </tx:attributes>
48.     </tx:advice>
49.     <!--配置AOP-->
50.     <aop:config>
51.         <!--配置切入点-->
52.         <aop:pointcut id="pt" expression="execution(*
    com.msb.service.AccountService.transMoney(..))"/>
53.         <!--配置切面-->
54.         <aop:advisor advice-ref="txAdvice" pointcut-ref="pt"></aop:advisor>
55.     </aop:config>
56. </beans> 






------------------------------------------------------------

