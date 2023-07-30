
# 6_Spring_Bean的自动装配

bean自动装配 




通过property标签可以手动指定给属性进行注入 

我们也可以通过自动转配,完成属性的自动注入,就是自动装配,可以简化DI的配置 







准备实体类 




1.  package com.msb.bean;
2.  /**
3.   * @Author: Ma HaiYang
4.   * @Description: MircoMessage:Mark_7001
5.   */
6.  public class Dept {
7.  }

 




1.  package com.msb.bean;
2.  /**
3.   * @Author: Ma HaiYang
4.   * @Description: MircoMessage:Mark_7001
5.   */
6.  public class Emp {
7.      private Dept dept;
8.      @Override
9.      public String toString() {
10.         return "Emp{" +
11.                 "dept=" + dept +
12.                 '}';
13.     }
14.     public Dept getDept() {
15.         return dept;
16.     }
17.     public void setDept(Dept dept) {
18.         this.dept = dept;
19.     }
20.     public Emp() {
21.     }
22.     public Emp(Dept dept) {
23.         this.dept = dept;
24.     }
25. }

 




配置文件 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <beans xmlns="http://www.springframework.org/schema/beans"
3.         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
4.         xmlns:p="http://www.springframework.org/schema/p"
5.         xmlns:c="http://www.springframework.org/schema/c"
6.         xsi:schemaLocation="http://www.springframework.org/schema/beans
7.         http://www.springframework.org/schema/beans/spring-beans.xsd">
8.      <bean id="dept" class="com.msb.bean.Dept"></bean>
9.      <!--
10.     autowire 属性控制自动将容器中的对象注入到当前对象的属性上
11.     byName 根据目标id值和属性值注入,要保证当前对象的属性值和目标对象的id值一致
12.     byType 根据类型注入,要保证相同类型的目标对象在容器中只有一个实例
13.     -->
14.     <bean id="emp" class="com.msb.bean.Emp" autowire="byName"></bean>
15. </beans> 




测试代码 




1.  package com.msb.test;
2.  import com.msb.bean.Emp;
3.  import com.msb.bean.User;
4.  import org.junit.Test;
5.  import org.springframework.context.support.ClassPathXmlApplicationContext;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. public class Test2 {
11.     @Test
12.     public void testGetBean(){
13.         ClassPathXmlApplicationContext context =new
    ClassPathXmlApplicationContext("applicationContext2.xml");
14.         Emp emp = context.getBean("emp", Emp.class);
15.         System.out.println(emp);
16.     }
17. } 















------------------------------------------------------------

