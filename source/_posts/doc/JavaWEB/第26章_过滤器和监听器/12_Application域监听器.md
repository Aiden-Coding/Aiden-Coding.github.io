
# 12_Application域监听器

### 认识Application域监听器 

Application域共有两个监听器接口,分别是 

ServletContextListener
ServletContextAttributeListener 

接下来我们就认识一些每个接口和接口中每个方法的用处 

**监听器代码** 

  




1.  package com.msb.listener;
2.  import javax.servlet.ServletContextAttributeEvent;
3.  import javax.servlet.ServletContextAttributeListener;
4.  import javax.servlet.ServletContextEvent;
5.  import javax.servlet.ServletContextListener;
6.  /**
7.   * @Author: Ma HaiYang
8.   * @Description: MircoMessage:Mark_7001
9.   */
10. public class MyApplicationListener implements ServletContextListener ,
    ServletContextAttributeListener {
11.     @Override
12.     public void contextInitialized(ServletContextEvent sce) {
13.         System.out.println("ServletContext创建并初始化了");
14.     }
15.     @Override
16.     public void contextDestroyed(ServletContextEvent sce) {
17.         System.out.println("ServletContext销毁了");
18.     }
19.     @Override
20.     public void attributeAdded(ServletContextAttributeEvent scae) {
21.         System.out.println("ServletContext增加了数据");
22.     }
23.     @Override
24.     public void attributeRemoved(ServletContextAttributeEvent scae) {
25.         System.out.println("ServletContext删除了数据");
26.     }
27.     @Override
28.     public void attributeReplaced(ServletContextAttributeEvent scae) {
29.         System.out.println("ServletContext修改了数据");
30.     }
31. }

 






------------------------------------------------------------

