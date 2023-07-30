
# 10_Request域监听器

### 认识Requet域监听器 

Requet域共有两个监听器接口,分别是 

ServletRequestListener  

ServleRequestAttributeListener 

接下来我们就认识一些每个接口和接口中每个方法的用处 

**定义监听器类** 

**
**

1.  **package com.msb.listener;**
2.  **import javax.servlet.*;**
3.  **/****
4.  ** * @Author: Ma HaiYang**
5.  ** * @Description: MircoMessage:Mark_7001**
6.  ** */**
7.  **public class MyRequestListener implements ServletRequestListener,
    ServletRequestAttributeListener {**
8.  **    @Override**
9.  **    public void requestDestroyed(ServletRequestEvent sre) {**
10. **        // 监听HttpServletRequest对象的销毁  项目中任何一个Request对象的销毁都会触发该方法的执行**
11. **        ServletRequest servletRequest = sre.getServletRequest();**
12. **        System.out.println("request"+servletRequest.hashCode()+"对象销毁了");**
13. **    }**
14. **    @Override**
15. **    public void requestInitialized(ServletRequestEvent sre) {**
16. **        // 监听HttpServletRequest对象的创建并初始化 项目中任何一个Request对象的创建并初始化都会触发该方法的执行**
17. **        ServletRequest servletRequest = sre.getServletRequest();**
18. **        System.out.println("request"+servletRequest.hashCode()+"对象初始化");**
19. **    }**
20. **    @Override**
21. **    public void attributeAdded(ServletRequestAttributeEvent srae) {**
22. **        // 任何一个Request对象中调用 setAttribute方法增加了数据都会触发该方法**
23. **        ServletRequest servletRequest = srae.getServletRequest();**
24. **        String name = srae.getName();**
25. **        Object value = srae.getValue();**
26. **       
    System.out.println("request"+servletRequest.hashCode()+"对象增加了数据:"+name+"="+v
    lue);**
27. **    }**
28. **    @Override**
29. **    public void attributeRemoved(ServletRequestAttributeEvent srae) {**
30. **       // 任何一个Request对象中调用 removeAttribute方法移除了数据都会触发该方法**
31. **        ServletRequest servletRequest = srae.getServletRequest();**
32. **        String name = srae.getName();**
33. **        Object value = srae.getValue();**
34. **       
    System.out.println("request"+servletRequest.hashCode()+"对象删除了数据:"+name+"="+v
    lue);**
35. **    }**
36. **    @Override**
37. **    public void attributeReplaced(ServletRequestAttributeEvent srae) {**
38. **        // 任何一个Request对象中调用 setAttribute方法修改了数据都会触发该方法**
39. **        ServletRequest servletRequest = srae.getServletRequest();**
40. **        String name = srae.getName();**
41. **        Object value = srae.getValue();**
42. **        Object newValue=servletRequest.getAttribute(name);**
43. **       
    System.out.println("request"+servletRequest.hashCode()+"对象增修改了数据:"+name+"="+
    alue+"设置为:"+newValue);**
44. **    }**
45. **}**

** **

**配置监听器  使用web.xml 或者通过@WebListener注解都可以 **

**
**

1.  **<?xml version="1.0" encoding="UTF-8"?>**
2.  **<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"**
3.  **         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"**
4.  **         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
    http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"**
5.  **         version="4.0">**
6.  **    **
7.  **    <listener>**
8.  **        <listener-class>com.msb.listener.MyRequestListener</listener-class>**
9.  **    </listener>**
10. **</web-app> **

**
**

**准备Servlet **

**
**

1.  **@WebServlet(urlPatterns = "/myServlet3.do")**
2.  **public class MyServlet3 extends HttpServlet {**
3.  **    @Override**
4.  **    protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {**
5.  **        req.setAttribute("name", "zhangsan");**
6.  **        req.setAttribute("name", "lisi");**
7.  **        req.removeAttribute("name");**
8.  **    }**
9.  **} **

**
**

**
**

**请求测试:略 **

**
**



------------------------------------------------------------

