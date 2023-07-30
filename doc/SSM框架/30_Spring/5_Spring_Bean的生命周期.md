
# 5_Spring_Bean的生命周期




bean从创建到销毁经历的各个阶段以及每个阶段所调用的方法 

1 通过构造器创建bean实例           执行构造器 

2 为bean属性赋值                         执行set方法 

3 初始化bean                                调用bean的初始化方法,需要配置指定调用的方法 

4 bean的获取                                容器对象 getBean方法 

5 容器关闭销毁bean                      调用销毁方法,需要配置指定调用的方法 




测试生命周期 

准备bean 




1.  package com.msb.bean;
2.  /**
3.   * @Author: Ma HaiYang
4.   * @Description: MircoMessage:Mark_7001
5.   */
6.  **public** **class** **User** {
7.      **private** Integer userid;
8.      **private** String username;
9.      **private** String password;
10.     **public** **void** **initUser**(){
11.         System.**out**.println("第三步:User初始化");
12.     }
13.     **public** **User**() {
14.         System.**out**.println("第一步:User构造");
15.     }
16.     **public** **void** **destoryUser**(){
17.         System.**out**.println("第五步:User销毁");
18.     }
19.     @Override
20.     **public** String **toString**() {
21.         **return** "User{" +
22.                 "userid=" + userid +
23.                 ", username='" + username + '\'' +
24.                 ", password='" + password + '\'' +
25.                 '}';
26.     }
27.     **public** **User**(Integer userid, String username, String password) {
28.         **this**.userid = userid;
29.         **this**.username = username;
30.         **this**.password = password;
31.     }
32.     **public** **void** **setUserid**(Integer userid) {
33.         System.**out**.println("setUserid");
34.         **this**.userid = userid;
35.     }
36.     **public** **void** **setUsername**(String username) {
37.         System.**out**.println("第二步:User属性赋值");
38.         **this**.username = username;
39.     }
40.     **public** **void** **setPassword**(String password) {
41.         **this**.password = password;
42.     }
43. }

 




配置bean 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <**beans** xmlns="http://www.springframework.org/schema/beans"
3.         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
4.         xmlns:p="http://www.springframework.org/schema/p"
5.         xmlns:c="http://www.springframework.org/schema/c"
6.         xsi:schemaLocation="http://www.springframework.org/schema/beans
7.         http://www.springframework.org/schema/beans/spring-beans.xsd">
8.      <**bean** id="user" class="com.msb.bean.User" init-method="initUser"
    destroy-method="destoryUser">
9.          <**property** name="username" value="xiaoming"></**property**>
10.     </**bean**>
11. </**beans**> 




测试bean  




1.  **package** com.msb.test;
2.  **import** com.msb.bean.User;
3.  **import** org.junit.Test;
4.  **import** org.springframework.context.ApplicationContext;
5.  **import** org.springframework.context.support.ClassPathXmlApplicationContext;
6.  /**
7.   * **@Author**: Ma HaiYang
8.   * **@Description**: MircoMessage:Mark_7001
9.   */
10. **public** **class** **Test1** {
11.     @Test
12.     **public** **void** **testGetBean**(){
13.         ClassPathXmlApplicationContext context =**new**
    ClassPathXmlApplicationContext("applicationContext.xml");
14.         User user = context.getBean("user",User.class);
15.         System.out.println("第四步:User对象从容器中获取");
16.         // 关闭容器
17.         context.close();
18.     }
19. }

 







关于后置处理器 




1 通过构造器创建bean实例           执行构造器 

2 为bean属性赋值                         执行set方法 

3 把bean实例传递给bean的后置处理器的方法 

4 初始化bean                                调用bean的初始化方法,需要配置指定调用的方法 

5 把bean实例传递给bean的后置处理器的方法 

6 bean的获取                                容器对象 getBean方法 

7 容器关闭销毁bean                      调用销毁方法,需要配置指定调用的方法 







1 创建后置处理器 实现 BeanPostProcesser  重写两个方法 




1.  package com.msb.beanProcesser;
2.  import org.springframework.beans.BeansException;
3.  import org.springframework.beans.factory.config.BeanPostProcessor;
4.  /**
5.   * @Author: Ma HaiYang
6.   * @Description: MircoMessage:Mark_7001
7.   */
8.  public class MyBeanProcesser implements BeanPostProcessor {
9.      @Override
10.     public Object postProcessBeforeInitialization(Object bean, String
    beanName) throws BeansException {
11.         //Object bean      实例化的bean
12.         //String beanName  bean的id
13.         System.out.println("bean:初始化方法之前");
14.         return bean;// 这里必须return bean
15.     }
16.     @Override
17.     public Object postProcessAfterInitialization(Object bean, String
    beanName) throws BeansException {
18.         System.out.println("bean:初始化方法之后");
19.         return bean;// 这里必须returnbean
20.     }
21. }

 




2 配置后置处理器,对容器中的所有bean添加后置处理器的生命周期 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <beans xmlns="http://www.springframework.org/schema/beans"
3.         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
4.         xmlns:p="http://www.springframework.org/schema/p"
5.         xmlns:c="http://www.springframework.org/schema/c"
6.         xsi:schemaLocation="http://www.springframework.org/schema/beans
7.         http://www.springframework.org/schema/beans/spring-beans.xsd">
8.      <bean id="user" class="com.msb.bean.User" init-method="initUser"
    destroy-method="destoryUser">
9.          <property name="username" value="xiaoming"></property>
10.     </bean>
11.     <bean id="myBeanProcesser"
    class="com.msb.beanProcesser.MyBeanProcesser"></bean>
12. </beans> 

BeanPostProcessor接口作用： 

    
如果我们想在Spring容器中完成bean实例化、配置以及其他初始化方法前后要添加一些自己逻辑处理。我们需要定义一个或多个BeanPostProcessor接口
现类，然后注册到Spring IoC容器中。 

1、接口中的两个方法都要将传入的bean返回，而不能返回null，如果返回的是null那么我们通过getBean方法将得不到目标。 

2、ApplicationContext会自动检测在配置文件中实现了BeanPostProcessor接口的所有bean，并把它们注册为后置处理器，然后在容器创建bean的适当时候调用它，因此部署一个后置处理器同部署其他的bean并没有什么区别。而使用BeanFactory实现的时候，bean 后置处理器必须通过代码显式地去注册，在IoC容器继承体系中的ConfigurableBeanFactory接口中定义了注册方法


























------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
