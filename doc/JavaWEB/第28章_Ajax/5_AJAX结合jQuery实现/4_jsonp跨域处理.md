
# 4_jsonp跨域处理

### jsonp跨域处理 

#### 4.4.1 什么是跨域? 

出于浏览器的同源策略限制。同源策略（Sameoriginpolicy）是一种约定，它是浏览器最核心也最基本的安全功能，如果缺少了同源策略，则浏览器的正常功能可能都会受到影响。可以说Web是构建在同源策略基础之上的，浏览器只是针对同源策略的一种实现。同源策略会阻止一个域的javascript脚本和另外一个域的内容进行交互。所谓同源（即指在同一个域）就是两个页面具有相同的协议（protocol），主机（host）和端口号（port）
**本地路径地址：
[http://127.0.0.1:8080/msb/index.jsp](https://127.0.0.1:8080/sxt/index.jsp)** 

[https](https://127.0.0.1:8080/sxt/index.jsp)
[://127.0.0.1:8080/msb/index.jsp](https://127.0.0.1:8080/sxt/index.jsp)** 协议不一样** 

[http://](http://192.168.24.11:8080/sxt/index.jsp)
[192.168.24.11](http://192.168.24.11:8080/sxt/index.jsp)
[:8080/msb/index.jsp](http://192.168.24.11:8080/sxt/index.jsp)** IP不一致** 

[http://127.0.0.1:](http://127.0.0.1:8888/sxt/index.jsp)
[8888](http://127.0.0.1:8888/sxt/index.jsp)
[/msb/index.jsp](http://127.0.0.1:8888/sxt/index.jsp)** 端口不一致** 

[http://](http://localhost:8080/sxt/index.jsp)
[localhost](http://localhost:8080/sxt/index.jsp)
[:8080/msb/index.jsp](http://localhost:8080/sxt/index.jsp)** IP不一致** 

演示代码如下 

使用Hbuider编写如下代码   




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
18.                        
    url:"http://localhost:8080/ajaxDemo3_war_exploded/unameCheckServlet.do?",
    // 请求的后台服务的路径
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

 

浏览器请求该资源的地址是: 

[http://127.0.0.1:8020/testa/index.html](http://127.0.0.1:8020/testa/index.html)
 

但是其内部ajax请求的资源的是: 

http://localhost:8080/ajaxDemo3_war_exploded/unameCheckServlet.do?  

二者端口号和IP其实是不一致的,这就受到同源策略的控制 





![image](data:image/png;base64,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)
#### 实现的原理是什么? 

我们发现Web页面上调用js文件时则不受是否跨域的影响,拥有”src”这个属性的标签都却拥有跨域的能力，比如<\script>、<\img>、<\iframe>
。那么跨域访问数据就有了一种可能，那就是在远程服务器上设法把数据装进js格式的文件里，供客户端调用和进一步处理。就好比使用一个<script>,让其src属性指向我们要访问的跨域资源
,然后以接收js文件的形式接收数据 

#### 通过:dataType:'jsonp'属性实现跨域请求 

 ** 通过 jsonp:'callback',属性简化回调函数处理** 

通过 jsonp:’callback’,实现自动处理回调函数名,相当于在url地址栏最后后拼接一个callback=函数名,后台自动根据这个函数名处理JS脚本,jQuery
也会根据这函数名自动在前端处理回调函数,这样我们直接在success方法中接收返回的数据即可,可以不用自己去自己定义回调函数.后台获取参数时,参数名要要和jsonp:
后面的函数名保持一致 

页面代码 




1.  <html>
2.  <head>
3.      <title>$Title%sSourceCode%lt;/title>
4.      <meta charset="UTF-8"/>
5.      <script
    src="http://localhost:8080/ajaxDemo3_war_exploded/js/jquery.min.js"></script
    
6.      <script>
7.      	
8.      	
9.          function checkUname(){
10.             // 获取输入框中的内容
11.             if(null == $("#unameI").val() || '' == $("#unameI").val()){
12.                 $("#unameInfo").text("用户名不能为空");
13.                 return;
14.             }
15.             $("#unameInfo").text("");
16.             // 通过jQuery.ajax() 发送异步请求
17.             $.ajax(
18.                 {
19.                     type:"GET",// 请求的方式 GET  POST
20.                    
    url:"http://localhost:8080/ajaxDemo3_war_exploded/unameCheckServlet.do?",
    // 请求的后台服务的路径
21.                     data:{uname:$("#unameI").val()},// 提交的参数
22.                     dataType:"jsonp",
23.                     jsonp:"aaa",
24.                     success:function(info){
25.                     	$("#unameInfo").text(info)
26.                     }
27.                     
28.                 }
29.             )
30.         }
31.         
32.         	
33.         
34.     </script>
35. </head>
36. <body>
37. <form action="myServlet1.do" >
38.     用户名:<input id="unameI" type="text" name="uname" onblur="checkUname()">
39.     <span id="unameInfo" style="color: red"></span><br/>
40.     密码:<input type="password" name="pwd"><br/>
41.     <input type="submit" value="提交按钮">
42. </form>
43. </body>
44. </html>

 




后端代码 




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
17.         String callBack = req.getParameter("aaa");
18.         System.out.println(uname);
19.         String info="";
20.         if("msb".equals(uname)){
21.             info="用户名已经占用";
22.         }else{
23.             info="用户名可用";
24.         }
25.         // 向浏览器响应数据
26.         resp.setCharacterEncoding("UTF-8");
27.         resp.setContentType("text/javaScript;charset=UTF-8");
28.         resp.getWriter().print(callBack+"('"+info+"')");
29.     }
30. }

 




#### 通过getJson方实现跨域请求 

getJSON方法是可以实现跨域请求的,在用该方法实现跨域请求时,在传递参数上应该注意在url后拼接一个jsoncallback=?,jQuery会自动替换?为正确的回调函数名
,我们就可以不用单独定义回调函数了 

 前端代码 




1.  <html>
2.  <head>
3.      <title>$Title%sSourceCode%lt;/title>
4.      <meta charset="UTF-8"/>
5.      <script
    src="http://localhost:8080/ajaxDemo3_war_exploded/js/jquery.min.js"></script
    
6.      <script>
7.      	
8.      	
9.          function checkUname(){
10.             // 获取输入框中的内容
11.             if(null == $("#unameI").val() || '' == $("#unameI").val()){
12.                 $("#unameInfo").text("用户名不能为空");
13.                 return;
14.             }
15.             $("#unameInfo").text("");
16.          
17.            $.getJSON(
18.            
    "http://localhost:8080/ajaxDemo3_war_exploded/unameCheckServlet.do?jsoncallb
    ck=?",
19.            	{uname:$("#unameI").val()},
20.            	function(info){
21.            		$("#unameInfo").text(info)
22.            	}
23.            	
24.            )
25.         }
26.         
27.         	
28.         
29.     </script>
30. </head>
31. <body>
32. <form action="myServlet1.do" >
33.     用户名:<input id="unameI" type="text" name="uname" onblur="checkUname()">
34.     <span id="unameInfo" style="color: red"></span><br/>
35.     密码:<input type="password" name="pwd"><br/>
36.     <input type="submit" value="提交按钮">
37. </form>
38. </body>
39. </html>

 




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
17.         String callBack = req.getParameter("jsoncallback");
18.         System.out.println(uname);
19.         String info="";
20.         if("msb".equals(uname)){
21.             info="用户名已经占用";
22.         }else{
23.             info="用户名可用";
24.         }
25.         // 向浏览器响应数据
26.         resp.setCharacterEncoding("UTF-8");
27.         resp.setContentType("text/javaScript;charset=UTF-8");
28.         resp.getWriter().print(callBack+"('"+info+"')");
29.     }
30. }

 




拓展:通过后台代码也可以实现跨域,一般在过滤器中添加如下代码,那么前端在请求时就不用考虑跨域问题了 

1.  ### /*请求地址白名单 *代表所有    */
2.  ###   resp.setHeader("Access-Control-Allow-Origin", "*");
3.  ###   /*请求方式白名单      */
4.  ###   resp.setHeader("Access-Control-Allow-Methods", "POST, GET, OPTIONS,
    DELETE");
5.  ###   resp.setHeader("Access-Control-Max-Age", "3600");
6.  ###   resp.setHeader("Access-Control-Allow-Headers", "x-requested-with"); 

### 

















































------------------------------------------------------------

