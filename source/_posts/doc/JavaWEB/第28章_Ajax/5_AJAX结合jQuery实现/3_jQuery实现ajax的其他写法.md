
# 3_jQuery实现ajax的其他写法

### jQuery实现AJAX的其他写法 

#### 4.3.1 $.load() 

jQuery load() 方法是简单但强大的 AJAX 方法，load() **方法从服务器加载数据，并把返回的数据放入被选元素中**。默认使用 GET 方式
\- 传递附加参数时自动转换为 POST 方式, 

语法为:   


|                                         |$(selector).load(URL,data,callback);     |

 参数的含义为:   


|                                                   |url: URL地址                                         |data:待发送参数。                                        |callback:载入成功时回调函数。                                |

  

  

测试代码 

准备第一个页面   




1.  <!DOCTYPE html>
2.  <html lang="en">
3.  <head>
4.      <meta charset="UTF-8">
5.      <title>Title</title>
6.      <script src="js/jquery.min.js"></script>
7.      <script>
8.          function testLoad(){
9.             
    //$("#d1").load("servlet2.do","username=aaa&password=bbb",function(){alert("
    应结束")})
10.             $("#d1").load("loadPage.html #a")
11.         }
12.     </script>
13. </head>
14. <body>
15. <div id="d1" style="width: 100px;height: 100px;border: 1px solid black">
16. </div>
17. <input type="button" value="测试" onclick="testLoad()">
18. </body>
19. </html> 

第二个页面 




1.  <!DOCTYPE html>
2.  <html lang="en">
3.  <head>
4.      <meta charset="UTF-8">
5.      <title>Title</title>
6.  </head>
7.  <body>
8.  <div id="a">
9.      <li>JAVA</li>
10.     <li>HTML</li>
11.     <li>CSS</li>
12.     <li>Mysql</li>
13.     <li>python</li>
14. </div>
15. </body>
16. </html> 

后台代码 




1.  package com.msb.servlet;
2.  import com.google.gson.Gson;
3.  import com.google.gson.GsonBuilder;
4.  import com.msb.pojo.Student;
5.  import javax.servlet.ServletException;
6.  import javax.servlet.annotation.WebServlet;
7.  import javax.servlet.http.HttpServlet;
8.  import javax.servlet.http.HttpServletRequest;
9.  import javax.servlet.http.HttpServletResponse;
10. import java.io.IOException;
11. import java.util.ArrayList;
12. import java.util.Collections;
13. import java.util.Date;
14. /**
15.  * @Author: Ma HaiYang
16.  * @Description: MircoMessage:Mark_7001
17.  */
18. @WebServlet("/servlet2.do")
19. public class Servlet2 extends HttpServlet {
20.     @Override
21.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
22.         String username = req.getParameter("username");
23.         String password = req.getParameter("password");
24.         System.out.println(username);
25.         System.out.println(password);
26.         resp.setContentType("text/html;charset=UTF-8");
27.         resp.setCharacterEncoding("UTF-8");
28.         resp.getWriter().print("<h1>hello</h1>");
29.     }
30. }

 




  

#### 4.3.1 $.get() 

这是一个简单的 GET 请求功能以取代复杂 $.ajax 。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用$.ajax。 

语法为:   


|                                        |$.get(url,[data],[callback],[type])     |

  

参数的含义为:   


|                                                                                                         |url: URL地址                                                                                               |data:待发送参数。                                                                                              |callback:载入成功时回调函数。                                                                                      |type:返回内容格式，xml, html, script, json, text, _default                                                      |

该函数是简写的 Ajax 函数，等价于：   


|                                                                                                            |$.ajax({                                                                                                    | type:   'GET',                                                                                             |  url: url,                                                                                                 |  data: data,                                                                                               |  success: success,                                                                                         |  dataType: dataType                                                                                        |});                                                                                                         |




#### 4.3.1 $.getJSON() 

JSON是一种较为理想的数据传输格式，它能够很好的融合与JavaScript或其他宿主语言，并且可以被JS直接使用。使用JSON相比传统的通过 GET、POST
直接发送“裸体”数据，在结构上更为合理，也更为安全。至于jQuery的getJSON()函数，只是设置了JSON参数的ajax()函数的一个简化版本。语法为: 
 


|                                                                                                                                 |$.getJSON(                                                                                                                       |      url,             //请求URL                                                                                                   |      [data],          //传参，可选参数                                                                                                 |      [callback]       //回调函数，可选参数                                                                                               |    );                                                                                                                           |

该函数是简写的 Ajax 函数，等价于：   


|                                                                                           |$.ajax({                                                                                   |  url: url,                                                                                |  data: data,                                                                              |  success: callback,                                                                       |  dataType: json                                                                           |});                                                                                        |

仅仅是等效于上述函数,但是除此之外这个函数也是可以跨域使用的，相比get()、post()有一定优势。另外这个函数可以通过把请求url写 成"myurl?callback=X"
这种格式，让程序执行回调函数X。 

  


注意:$.getJSON是以GET方式提交数据，如果需要提交很大的数据量，可选$.post 

#### $.post() 

这是一个简单的 POST 请求功能以取代复杂 $.ajax 。请求成功时可调用回调函数。如果需要在出错时执行函数，请使用$.ajax。 

语法为:   


|                                         |$.post(url,[data],[callback],[type])     |

参数的含义为:   


|                                                                                                         |url: URL地址                                                                                               |data:待发送参数。                                                                                              |callback:载入成功时回调函数。                                                                                      |type:返回内容格式，xml, html, script, json, text, _default                                                      |

该函数是简写的 Ajax 函数，等价于：   


|                                                                                                                      |$.ajax({                                                                                                              |  type:   'POST',                                                                                                     |  url: url,                                                                                                           |  data: data,                                                                                                         |  success: success,                                                                                                   |  dataType: dataType                                                                                                  |});                                                                                                                   |                                                                                                                      |

前端代码 




1.  <!DOCTYPE html>
2.  <html lang="en">
3.  <head>
4.      <meta charset="UTF-8">
5.      <title>Title</title>
6.      <script src="js/jquery.min.js"></script>
7.      <script>
8.          function testAjax(){
9.              $.get(
10.                 "servlet1.do",
11.                 {"username":"zhangsan","password":"123456"},
12.                 function(list){
13.                     $.each(list,function(i,e){
14.                         console.log(e)
15.                     })
16.                  },
17.                 "json")
18.             console.log("------------------------------")
19.             $.getJSON(
20.                 "servlet1.do",
21.                 {"username":"zhangsan","password":"123456"},
22.                 function(list){
23.                     $.each(list,function(i,e){
24.                         console.log(e)
25.                     })
26.                 })
27.             console.log("------------------------------")
28.             $.post(
29.                 "servlet1.do",
30.                 {"username":"zhangsan","password":"123456"},
31.                 function(list){
32.                     $.each(list,function(i,e){
33.                         console.log(e)
34.                     })
35.                 },
36.                 "json")
37.         }
38.     </script>
39. </head>
40. <body>
41. <input type="button" value="测试" onclick="testAjax()">
42. </body>
43. </html> 




后端代码 




1.  package com.msb.servlet;
2.  import com.google.gson.Gson;
3.  import com.google.gson.GsonBuilder;
4.  import com.msb.pojo.Student;
5.  import sun.util.calendar.LocalGregorianCalendar;
6.  import javax.servlet.ServletException;
7.  import javax.servlet.annotation.WebServlet;
8.  import javax.servlet.http.HttpServlet;
9.  import javax.servlet.http.HttpServletRequest;
10. import javax.servlet.http.HttpServletResponse;
11. import java.io.IOException;
12. import java.util.ArrayList;
13. import java.util.Collections;
14. import java.util.Date;
15. /**
16.  * @Author: Ma HaiYang
17.  * @Description: MircoMessage:Mark_7001
18.  */
19. @WebServlet("/servlet1.do")
20. public class Servlet1 extends HttpServlet {
21.     @Override
22.     protected void service(HttpServletRequest req, HttpServletResponse
    resp) throws ServletException, IOException {
23.         String username = req.getParameter("username");
24.         String password = req.getParameter("password");
25.         System.out.println(username);
26.         System.out.println(password);
27.         Student stu1=new Student("小黑","男",10,new Date());
28.         Student stu2=new Student("小白","男",10,new Date());
29.         Student stu3=new Student("小黄","男",10,new Date());
30.         Student stu4=new Student("小花","男",10,new Date());
31.         ArrayList<Student> list =new ArrayList<>();
32.         Collections.addAll(list,stu1,stu2,stu3,stu4);
33.         GsonBuilder gb =new GsonBuilder();
34.         gb.setDateFormat("yyyy-MM-dd");
35.         Gson gson = gb.create();
36.         String json = gson.toJson(list);
37.         resp.setContentType("text/html;charset=UTF-8");
38.         resp.setCharacterEncoding("UTF-8");
39.         resp.getWriter().print(json);
40.     }
41. }

 









------------------------------------------------------------

