
# 3_Session域

### Session域 

**有效范围** 

单次会话内有效,可以跨多个请求 

**生命周期** 

创建 会话的产生,第一次发生请求,会话的开始 

使用 本次会话之内,浏览器和服务器之间发生多次请求和响应有效 

销毁 会话结束,如:浏览器失去JSESSIONID、到达最大不活动时间、手动清除 

**测试代码** 

Session域中放入数据   




1.  package com.msb.testSession;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.HttpServlet;
5.  import javax.servlet.http.HttpServletRequest;
6.  import javax.servlet.http.HttpServletResponse;
7.  import javax.servlet.http.HttpSession;
8.  import java.io.IOException;
9.  import java.util.ArrayList;
10. import java.util.Collections;
11. import java.util.List;
12. /**
13.  * @Author: Ma HaiYang
14.  * @Description: MircoMessage:Mark_7001
15.  */
16. @WebServlet(urlPatterns = "/addToSession.do")
17. public class Servlet1 extends HttpServlet {
18.     @Override
19.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
20.         // 向Session域中添加数据
21.         HttpSession session = req.getSession();
22.         List<String> x=new ArrayList<>();
23.         Collections.addAll(x, "a","b","c");
24.         session.setAttribute("list", x);
25.         session.setAttribute("gender","boy");
26.         session.setAttribute("gender","girl");
27.         session.setAttribute("name","晓明");
28.         // 重定向
29.         resp.sendRedirect("readFromSession.do");
30.     }
31. }

 




从Session域中读取数据   




1.  package com.msb.testSession;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.HttpServlet;
5.  import javax.servlet.http.HttpServletRequest;
6.  import javax.servlet.http.HttpServletResponse;
7.  import javax.servlet.http.HttpSession;
8.  import java.io.IOException;
9.  import java.util.List;
10. /**
11.  * @Author: Ma HaiYang
12.  * @Description: MircoMessage:Mark_7001
13.  */
14. @WebServlet(urlPatterns="/readFromSession.do")
15. public class Servlet2 extends HttpServlet {
16.     @Override
17.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
18.         HttpSession session = req.getSession();
19.         // 移除域中的互数据
20.         //session.removeAttribute("gender");
21.         // 从request域中读取数据
22.         List<String> list =(List<String>) session.getAttribute("list");
23.         System.out.println(list);
24.         System.out.println(session.getAttribute("gender"));
25.         System.out.println(session.getAttribute("name"));
26.         //获取Request中的请求参数
27.         System.out.println(req.getParameter("username"));
28.         System.out.println(req.getParameter("password"));
29.     }
30. }






------------------------------------------------------------

