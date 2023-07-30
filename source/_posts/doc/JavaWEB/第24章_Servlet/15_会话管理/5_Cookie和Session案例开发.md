
# 5_Cookie和Session案例开发

### 案例:通过HttpSession判断用户是否登录 

需求:实现登录一次即可,在一次会话内,可以反复多次访问WEB-INF/ welcome.html,如果没有登录过,跳转到登录页,登录成功后,可以访问 

项目结构: 


![image](data:image/png;base64,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)
组件介绍: 

login.html 




1.  <!DOCTYPE html>
2.  <html lang="en">
3.  <head>
4.      <meta charset="UTF-8">
5.      <title>Title</title>
6.  </head>
7.  <body>
8.  <form method="get" action="loginServlet.do">
9.      用户名:<input type="text" name="username" ><br/>
10.     密码:<input type="password" name="password" ><br/>
11.     <input type="submit" >
12. </form>
13. </body>
14. </html> 




登录成功之后可以访问的资源 

main.html 




1.  <!DOCTYPE html>
2.  <html lang="en">
3.  <head>
4.      <meta charset="UTF-8">
5.      <title>Title</title>
6.  </head>
7.  <body>
8.     this is main page
9.  </body>
10. </html> 







LoginServlet  

用来校验登录的,登录成功将用户信息存户HttpSession,否则回到登录页 




1.  package com.msb.servlet;
2.  import com.msb.pojo.User;
3.  import javax.servlet.ServletException;
4.  import javax.servlet.annotation.WebServlet;
5.  import javax.servlet.http.HttpServlet;
6.  import javax.servlet.http.HttpServletRequest;
7.  import javax.servlet.http.HttpServletResponse;
8.  import javax.servlet.http.HttpSession;
9.  import java.io.IOException;
10. /**
11.  * @Author: Ma HaiYang
12.  * @Description: MircoMessage:Mark_7001
13.  */
14. @WebServlet(urlPatterns = "/loginServlet.do")
15. public class LoginServlet extends HttpServlet {
16.     @Override
17.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
18.         // 获取用户名和密码
19.         String username = req.getParameter("username");
20.         String password = req.getParameter("password");
21.         // 如果用户名和密码为 msb 1234
22.         if("msb".equals(username)  && "1234".equals(password)){
23.             // 将用户信息放在HTTPSession中
24.             User user =new User(null, null, "msb", "1234");
25.             HttpSession session = req.getSession();
26.             session.setAttribute("user", user);
27.             // 登录成功 跳转至 main.html
28.             resp.sendRedirect(req.getContextPath()+"/mainServlet.do");
29.         }else{
30.             // 登录失败 回到login.html
31.             resp.sendRedirect(req.getContextPath()+"/login.html");
32.         }
33.     }
34. }

 




MainServlet 

用来向main.html中跳转的,同时验证登录,登录过,可以直接跳转,否则回到登录页 




1.  package com.msb.servlet;
2.  import com.msb.pojo.User;
3.  import javax.servlet.ServletException;
4.  import javax.servlet.annotation.WebServlet;
5.  import javax.servlet.http.HttpServlet;
6.  import javax.servlet.http.HttpServletRequest;
7.  import javax.servlet.http.HttpServletResponse;
8.  import javax.servlet.http.HttpSession;
9.  import java.io.IOException;
10. import java.util.logging.Handler;
11. /**
12.  * @Author: Ma HaiYang
13.  * @Description: MircoMessage:Mark_7001
14.  */
15. @WebServlet(urlPatterns = "/mainServlet.do")
16. public class MainServlet extends HttpServlet {
17.     @Override
18.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
19.         //跳转至main.html
20.         HttpSession session = req.getSession();
21.         User user = (User)session.getAttribute("user");
22.         if(null != user){
23.             // 判断如果登录过 允许跳转  HTTPSession中如果有登陆过的信息
24.            
    req.getRequestDispatcher("/WEB-INF/main.html").forward(req,resp);
25.         }else{
26.             // 如果没有登录过 回到登录去登录  HTTPSession中如果有登陆过的信息
27.             resp.sendRedirect("login.html");
28.         }
29.     }
30. }

 




User 

       用来存储一个用户的信息的实体类对象   




1.  public class User implements Serializable {
2.      private Integer uid;
3.      private String realname;
4.      private String username;
5.      private String pasword; 




  



------------------------------------------------------------

