
# 4_Application域

### Application域 

**有效范围** 

当前web服务内,跨请求,跨会话 

**生命周期** 

    创建 项目启动 

使用 项目运行任何时间有效 

销毁 项目关闭 

**测试代码** 

Application域中放入数据   




1.  package com.msb.testApplication;
2.  import javax.servlet.ServletContext;
3.  import javax.servlet.ServletException;
4.  import javax.servlet.annotation.WebServlet;
5.  import javax.servlet.http.HttpServlet;
6.  import javax.servlet.http.HttpServletRequest;
7.  import javax.servlet.http.HttpServletResponse;
8.  import javax.servlet.http.HttpSession;
9.  import java.io.IOException;
10. import java.util.ArrayList;
11. import java.util.Collections;
12. import java.util.List;
13. /**
14.  * @Author: Ma HaiYang
15.  * @Description: MircoMessage:Mark_7001
16.  */
17. @WebServlet(urlPatterns = "/addToApplication.do")
18. public class Servlet1 extends HttpServlet {
19.     @Override
20.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
21.         // 向Application域中添加数据
22.         ServletContext application = req.getServletContext();
23.         List<String> x=new ArrayList<>();
24.         Collections.addAll(x, "a","b","c");
25.         application.setAttribute("list", x);
26.         application.setAttribute("gender","girl");
27.         application.setAttribute("name","晓明");
28.     }
29. }

 




Application域中读取数据   




1.  package com.msb.testApplication;
2.  import javax.servlet.ServletContext;
3.  import javax.servlet.ServletException;
4.  import javax.servlet.annotation.WebServlet;
5.  import javax.servlet.http.HttpServlet;
6.  import javax.servlet.http.HttpServletRequest;
7.  import javax.servlet.http.HttpServletResponse;
8.  import javax.servlet.http.HttpSession;
9.  import java.io.IOException;
10. import java.util.List;
11. /**
12.  * @Author: Ma HaiYang
13.  * @Description: MircoMessage:Mark_7001
14.  */
15. @WebServlet(urlPatterns="/readFromApplication.do")
16. public class Servlet2 extends HttpServlet {
17.     @Override
18.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
19.         ServletContext application = this.getServletContext();
20.         // 从application域中读取数据
21.         List<String> list =(List<String>) application.getAttribute("list");
22.         System.out.println(list);
23.         System.out.println(application.getAttribute("gender"));
24.         System.out.println(application.getAttribute("name"));
25.     }
26. }






------------------------------------------------------------

