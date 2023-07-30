
# 7_案例开发之POST乱码处理

准备页面login.jsp 




1.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
2.  <html>
3.    <head>
4.      <title>$Title%sSourceCode%lt;/title>
5.    </head>
6.    <body>
7.    please login ... ... <br/>
8.    <form action="loginController.do" method="post">
9.      用户名:<input type="text" name="user"> <br/>
10.     密码:<input type="password" name="pwd"><br/>
11.     <input type="submit" value="提交">
12.   </form>
13.   </body>
14. </html>

 




准备servlet,LoginController 




1.  package com.msb.controller;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.HttpServlet;
5.  import javax.servlet.http.HttpServletRequest;
6.  import javax.servlet.http.HttpServletResponse;
7.  import java.io.IOException;
8.  /**
9.   * @Author: Ma HaiYang
10.  * @Description: MircoMessage:Mark_7001
11.  */
12. @WebServlet(urlPatterns = "/loginController.do")
13. public class LoginController extends HttpServlet {
14.     @Override
15.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
16.         // 获取用户名和密码
17.         String user = req.getParameter("user");
18.         String pwd = req.getParameter("pwd");
19.         System.out.println(user);
20.         System.out.println(pwd);
21.     }
22. }

 







准备过滤器 




1.  package com.msb.filter;
2.  import javax.servlet.*;
3.  import javax.servlet.annotation.WebFilter;
4.  import java.io.IOException;
5.  /**
6.   * @Author: Ma HaiYang
7.   * @Description: MircoMessage:Mark_7001
8.   */
9.  public class Filter0_EncodingFilter implements Filter {
10.     private String charset;
11.     @Override
12.     public void doFilter(ServletRequest servletRequest, ServletResponse
    servletResponse, FilterChain filterChain) throws IOException,
    ServletException {
13.         servletRequest.setCharacterEncoding(charset);
14.         // 放行
15.         filterChain.doFilter(servletRequest, servletResponse);
16.     }
17.     @Override
18.     public void init(FilterConfig filterConfig) throws ServletException {
19.         charset = filterConfig.getInitParameter("charset");
20.     }
21.     @Override
22.     public void destroy() {
23.     }
24. }

 







配置过滤器 




1.  <?xml version="1.0" encoding="UTF-8"?>
2.  <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
3.           xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
4.           xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
    http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
5.           version="4.0">
6.      <filter>
7.          <filter-name>encodingFilter</filter-name>
8.          <filter-class>com.msb.filter.Filter0_EncodingFilter</filter-class>
9.          <init-param>
10.             <param-name>charset</param-name>
11.             <param-value>UTF-8</param-value>
12.         </init-param>
13.     </filter>
14.     <filter-mapping>
15.         <filter-name>encodingFilter</filter-name>
16.         <url-pattern>*.do</url-pattern>
17.     </filter-mapping>
18. </web-app> 












------------------------------------------------------------

