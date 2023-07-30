
# 13_Spring_AOPXML方式实现_了解

1、创建两个类，增强类和被增强类，创建方法 




见之前的代码 




2、在spring配置文件中创建两个类对象 




1.  <!--创建对象--> 
2.  <bean id="userDao" class="com.com.msb.UserDaoImpl"></bean> 
3.  <bean id="daoAspect" class="com.com.aspect.DaoAspect"></bean> 

3、在spring配置文件中配置切入点 




1.   <!--配置aop增强-->
2.      <aop:config>
3.          <!--切入点-->
4.          <aop:pointcut id="pointCutAdd" expression="execution(*
    com.msb.dao.UserDao.add*(..))"/>
5.          <!--配置切面-->
6.          <aop:aspect ref="daoAspect">
7.              <!--增强作用在具体的方法上-->
8.              <aop:before method="methodBefore" pointcut-ref="pointCutAdd"/>
9.              <aop:after method="methodAfter" pointcut-ref="pointCutAdd"/>
10.             <aop:around method="methodAround" pointcut-ref="pointCutAdd"/>
11.             <aop:after-returning method="methodAfterReturning" 
    pointcut-ref="pointCutAdd" returning="res"/>
12.             <aop:after-throwing method="methodAfterThrowing" 
    pointcut-ref="pointCutAdd" throwing="ex"/>
13.         </aop:aspect>
14.     </aop:config> 






------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
