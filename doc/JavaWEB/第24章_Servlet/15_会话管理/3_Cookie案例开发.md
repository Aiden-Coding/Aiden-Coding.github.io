
# 3_Cookie案例开发

### 案例:通过Cookie判断用户是否访问过当前Servlet 

需求：当客户端浏览器第一次访问Servlet时返回“您好，欢迎您第一次访问！”，第二次访问时返回“欢迎您回来！” 




1.  package com.mashibing.test;
2.  import javax.servlet.ServletException;
3.  import javax.servlet.annotation.WebServlet;
4.  import javax.servlet.http.Cookie;
5.  import javax.servlet.http.HttpServlet;
6.  import javax.servlet.http.HttpServletRequest;
7.  import javax.servlet.http.HttpServletResponse;
8.  import java.io.IOException;
9.  /**
10.  * @Author: Ma HaiYang
11.  * @Description: MircoMessage:Mark_7001
12.  */
13. @WebServlet(urlPatterns = "/servlet3.do")
14. public class Servlet3 extends HttpServlet {
15.     @Override
16.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
17.         // 如果是第一访问当前Servlet.向浏览器响应一个cookie ("servlet3","1")
18.         // 如果是多次访问,就再次数上+1
19.         Cookie[] cookies = req.getCookies();
20.         boolean  flag =false ;
21.         if(null !=cookies){
22.             for (Cookie cookie : cookies) {
23.                 String cookieName = cookie.getName();
24.                 if(cookieName.equals("servlet3")){
25.                     // 创建Cookie次数+1
26.                     Integer value = Integer.parseInt(cookie.getValue())+1;
27.                     Cookie c=new Cookie("servlet3", String.valueOf(value));
28.                     resp.addCookie(c);
29.                     System.out.println("欢迎您第"+value+"访问");
30.                     flag=true;
31.                 }
32.             }
33.         }
34.         if(!flag){
35.             System.out.println("欢迎您第一次访问");
36.             Cookie c=new Cookie("servlet3", "1");
37.             resp.addCookie(c);
38.         }
39.     }
40. }

 




  



------------------------------------------------------------

