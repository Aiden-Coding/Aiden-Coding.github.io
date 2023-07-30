
# 1_jQuery_ajax_的简单使用

每次书写AJAX代码比较繁琐 步骤都是一样的,数据回显使用原生js代码也比较繁琐,可以使用jQuery对上述问题进行优化,jQuery不仅仅对dom操作进行了封装 同时也对
AJAX提交和回显已经进行了封装,可大大简化AJAX的操作步骤 


![image](data:image/png;base64,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)
### jQuery.ajax()的简单使用 

基本语法为(经典语法): 

前端代码 




1.  <html>
2.  <head>
3.      <title>$Title%sSourceCode%lt;/title>
4.      <meta charset="UTF-8"/>
5.      <script src="js/jquery.min.js"></script>
6.      <script>
7.          function checkUname(){
8.              // 获取输入框中的内容
9.              if(null == $("#unameI").val() || '' == $("#unameI").val()){
10.                 $("#unameInfo").text("用户名不能为空");
11.                 return;
12.             }
13.             $("#unameInfo").text("");
14.             // 通过jQuery.ajax() 发送异步请求
15.             $.ajax(
16.                     {
17.                         type:"GET",// 请求的方式 GET  POST
18.                         url:"unameCheckServlet.do?", // 请求的后台服务的路径
19.                         data:"uname="+$("#unameI").val(),// 提交的参数
20.                         success:function(info){ // 响应成功执行的函数
21.                             $("#unameInfo").text(info)
22.                         }
23.                     }
24.             )
25.         }
26.     </script>
27. </head>
28. <body>
29. <form action="myServlet1.do" >
30.     用户名:<input id="unameI" type="text" name="uname" onblur="checkUname()">
31.     <span id="unameInfo" style="color: red"></span><br/>
32.     密码:<input type="password" name="pwd"><br/>
33.     <input type="submit" value="提交按钮">
34. </form>
35. </body>
36. </html>

 







后台代码





1.  package com.msb.servlet;
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
12. @WebServlet("/unameCheckServlet.do")
13. public class UnameCheckServlet extends HttpServlet {
14.     @Override
15.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
16.         String uname = req.getParameter("uname");
17.         String info="";
18.         if("msb".equals(uname)){
19.             info="用户名已经占用";
20.         }else{
21.             info="用户名可用";
22.         }
23.         // 向浏览器响应数据
24.         resp.setCharacterEncoding("UTF-8");
25.         resp.setContentType("text/html;charset=UTF-8");
26.         resp.getWriter().print(info);
27.     }
28. }

 




**JSON格式处理** 

**前端代码** 

**
**

1.  **<!DOCTYPE html>**
2.  **<html lang="en">**
3.  **<head>**
4.  **    <meta charset="UTF-8">**
5.  **    <title>Title</title>**
6.  **    <script src="js/jquery.min.js"></script>**
7.  **    <script>**
8.  **        function testAjax(){**
9.  **            // 向后台发送一个ajax异步请求**
10. **            // 接收响应的数据**
11. **            $.ajax(**
12. **                {**
13. **                    type:"GET",**
14. **                    url:"servlet1.do",**
15. **                    data:{"username":"zhangsan","password":"123456"},//
    key=value&key=value  {"属性名":"属性值"}**
16. **                    dataType:"json",//以什么格式接收后端响应给我们的信息**
17. **                    success:function(list){**
18. **                        $.each(list,function(i,e){**
19. **                            console.log(e)**
20. **                        })**
21. **                    }**
22. **                }**
23. **            )**
24. **        }**
25. **    </script>**
26. **</head>**
27. **<body>**
28. **<input type="button" value="测试" onclick="testAjax()">**
29. **</body>**
30. **</html> **

**
**

**后台代码** 

**
**

1.  **package com.msb.servlet;**
2.  **import com.google.gson.Gson;**
3.  **import com.google.gson.GsonBuilder;**
4.  **import com.msb.pojo.Student;**
5.  **import sun.util.calendar.LocalGregorianCalendar;**
6.  **import javax.servlet.ServletException;**
7.  **import javax.servlet.annotation.WebServlet;**
8.  **import javax.servlet.http.HttpServlet;**
9.  **import javax.servlet.http.HttpServletRequest;**
10. **import javax.servlet.http.HttpServletResponse;**
11. **import java.io.IOException;**
12. **import java.util.ArrayList;**
13. **import java.util.Collections;**
14. **import java.util.Date;**
15. **/****
16. ** * @Author: Ma HaiYang**
17. ** * @Description: MircoMessage:Mark_7001**
18. ** */**
19. **@WebServlet("/servlet1.do")**
20. **public class Servlet1 extends HttpServlet {**
21. **    @Override**
22. **    protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {**
23. **        String username = req.getParameter("username");**
24. **        String password = req.getParameter("password");**
25. **        System.out.println(username);**
26. **        System.out.println(password);**
27. **        Student stu1=new Student("小黑","男",10,new Date());**
28. **        Student stu2=new Student("小白","男",10,new Date());**
29. **        Student stu3=new Student("小黄","男",10,new Date());**
30. **        Student stu4=new Student("小花","男",10,new Date());**
31. **        ArrayList<Student> list =new ArrayList<>();**
32. **        Collections.addAll(list,stu1,stu2,stu3,stu4);**
33. **        GsonBuilder gb =new GsonBuilder();**
34. **        gb.setDateFormat("yyyy-MM-dd");**
35. **        Gson gson = gb.create();**
36. **        String json = gson.toJson(list);**
37. **        resp.setContentType("text/html;charset=UTF-8");**
38. **        resp.setCharacterEncoding("UTF-8");**
39. **        resp.getWriter().print(json);**
40. **    }**
41. **}**

** **

**
**



------------------------------------------------------------

