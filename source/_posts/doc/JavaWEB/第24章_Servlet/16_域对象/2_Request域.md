
# 2_Request域

### 4.1 Request域 

**有效范围** 

一次请求内有效,请求转发时数据可以传递,除此之外该域没有办法实现数据共享 

**生命周期** 

创建 每发生一次请求创建一个独立的请求域 

使用service方法中或者请求转发有效 

销毁 请求结束,已经向浏览器响应数据 

**测试代码** 

向request域中放入数据   




1.  package com.msb.testRequest;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.HttpServlet;
5.  import javax.servlet.http.HttpServletRequest;
6.  import javax.servlet.http.HttpServletResponse;
7.  import java.io.IOException;
8.  import java.util.ArrayList;
9.  import java.util.Collections;
10. import java.util.List;
11. /**
12.  * @Author: Ma HaiYang
13.  * @Description: MircoMessage:Mark_7001
14.  */
15. @WebServlet(urlPatterns = "/addToRequest.do")
16. public class Servlet1 extends HttpServlet {
17.     @Override
18.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
19.         // 向request域中添加数据
20.         List<String> x=new ArrayList<>();
21.         Collections.addAll(x, "a","b","c");
22.         req.setAttribute("list", x);
23.         req.setAttribute("gender","boy");
24.         req.setAttribute("gender","girl");
25.         req.setAttribute("name","晓明");
26.         // 请求转发
27.          req.getRequestDispatcher("/readFromRequest.do").forward(req,resp);
28.         // 重定向
29.         //resp.sendRedirect("readFromRequest.do");
30.     }
31. }

 




**request域中读取数据**   




1.  package com.msb.testRequest;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.HttpServlet;
5.  import javax.servlet.http.HttpServletRequest;
6.  import javax.servlet.http.HttpServletResponse;
7.  import java.io.IOException;
8.  import java.util.List;
9.  /**
10.  * @Author: Ma HaiYang
11.  * @Description: MircoMessage:Mark_7001
12.  */
13. @WebServlet(urlPatterns="/readFromRequest.do")
14. public class Servlet2 extends HttpServlet {
15.     @Override
16.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
17.         // 移除域中的互数据
18.         req.removeAttribute("gender");
19.         // 从request域中读取数据
20.         List<String> list =(List<String>) req.getAttribute("list");
21.         System.out.println(list);
22.         System.out.println(req.getAttribute("gender"));
23.         System.out.println(req.getAttribute("name"));
24.         //获取Request中的请求参数
25.         System.out.println(req.getParameter("username"));
26.         System.out.println(req.getParameter("password"));
27.     }
28. }






------------------------------------------------------------

