
# 11_Session域监听器






Session域共有四个监听器接口,分别是 

HttpSessionListener
HttpSessionAttributeListener
HttpSessionBindingListener
HttpSessionActivationListener
接下来我们就认识一些每个接口和接口中每个方法的用处 

**监听器代码** 

HttpSessionListener
HttpSessionAttributeListener 

1.  package com.msb.listener;
2.  import javax.servlet.annotation.WebListener;
3.  import javax.servlet.http.HttpSessionAttributeListener;
4.  import javax.servlet.http.HttpSessionBindingEvent;
5.  import javax.servlet.http.HttpSessionEvent;
6.  import javax.servlet.http.HttpSessionListener;
7.  /**
8.   * @Author: Ma HaiYang
9.   * @Description: MircoMessage:Mark_7001
10.  */
11. @WebListener
12. public class MySessionListener implements HttpSessionListener ,
    HttpSessionAttributeListener {
13.     @Override
14.     public void sessionCreated(HttpSessionEvent se) {
15.         System.out.println("任何一个Session对象创建");
16.     }
17.     @Override
18.     public void sessionDestroyed(HttpSessionEvent se) {
19.         System.out.println("任何一个Session对象的销毁");
20.     }
21.     @Override
22.     public void attributeAdded(HttpSessionBindingEvent se) {
23.         System.out.println("任何一个Session对象中添加了数据");
24.     }
25.     @Override
26.     public void attributeRemoved(HttpSessionBindingEvent se) {
27.         System.out.println("任何一个Session对象中移除了数据");
28.     }
29.     @Override
30.     public void attributeReplaced(HttpSessionBindingEvent se) {
31.         System.out.println("任何一个Session对象中修改了数据");
32.     }
33. }

 

HttpSessionBindingListener 







1.  package com.msb.listener;
2.  import javax.servlet.http.HttpSessionBindingEvent;
3.  import javax.servlet.http.HttpSessionBindingListener;
4.  /**
5.   * @Author: Ma HaiYang
6.   * @Description: MircoMessage:Mark_7001
7.   */
8.  /*
9.  * 可以监听具体的某个session对象的事件的
10. *
11. * HttpSessionListener 只要在web.xml中配置或者通过@WebListener注解就可以注册监听所有的Session对象
12. \* HttpSessionBindingListener
    必须要通过setAttribute方法和某个session对象绑定之后,监听单独的某个Session对象
13. * */
14. public class MySessionBindingListener implements HttpSessionBindingListener
    {
15.     // 绑定方法
16.     /*
17.     session.setAttribute("mySessionBindingListener",new
    MySessionBindingListener())
18.      */
19.     @Override
20.     public void valueBound(HttpSessionBindingEvent event) {
21.         System.out.println("监听器和某个session对象绑定了");
22.     }
23.     // 解除绑定方法
24.     /*
25.     * 当发生如下情况,会触发该方法的运行
26.     * 1 session.invalidate(); 让session不可用
27.     * 2 session到达最大不活动时间,session对象回收 ;
28.     * 3 session.removeAttribute("mySessionBindingListener");手动解除绑定
29.     * */
30.     @Override
31.     public void valueUnbound(HttpSessionBindingEvent event) {
32.     }
33. }

 




HttpSessionActivationListener 




1.  package com.msb.listener;
2.  import javax.servlet.annotation.WebListener;
3.  import javax.servlet.http.HttpSessionActivationListener;
4.  import javax.servlet.http.HttpSessionEvent;
5.  /**
6.   * @Author: Ma HaiYang
7.   * @Description: MircoMessage:Mark_7001
8.   */
9.  
    
10. public class MySessionActivationListener implements
    HttpSessionActivationListener {
11.     @Override
12.     public void sessionWillPassivate(HttpSessionEvent se) {
13.         System.out.println("session即将钝化");
14.     }
15.     @Override
16.     public void sessionDidActivate(HttpSessionEvent se) {
17.         System.out.println("session活化完毕");
18.     }
19. }

 






------------------------------------------------------------

