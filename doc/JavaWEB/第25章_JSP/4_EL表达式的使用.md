
# 4_EL表达式的使用


Expression Language 

EL表达式中定义了一些可以帮助我们快捷从域对象中取出数据的写法,基本语法为   


|                       |${域标志.数据名.属性名(可选)}     |

**四个域标志关键字分别为** 

requestScope         request域 

sessionScope          session域 

applicationScope   application域 

pageScope             page域 

##### EL表达式取出域中的数据 




1.  <%@ page import="com.msb.pojo.User" %>
2.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
3.  <html>
4.  <head>
5.      <title>Title</title>
6.  </head>
7.  <body>
8.      <%--向pageContext域中放数据--%>
9.      <%
10.     pageContext.setAttribute("msg", "pageContextMessage");
11.     pageContext.setAttribute("userx", new User(1,"大黄","abcdefg"));
12.     %>
13.     <%--
14.     从域中取出数据
15.     El表达式在获取对象属性值得时候,是通过对象的属性的get方法获取的
16.     保证对象的要获取的属性必须有对应get方法才可以
17.     EL表达式在使用时是不需要import其他类的
18.     El如果获取的是NULL值,是不展示任何信息的
19.     --%>
20.     pageContext域中的数据:<br/>
21.     msg:${pageScope.msg}<br/>
22.     username:${pageScope.userx.name}<br/>
23.     <hr/>
24.     request域中的数据:<br/>
25.     msg:${requestScope.msg}<br/>
26.     username:${requestScope.user.name}<br/>
27.     <hr/>
28.     session域中的数据:<br/>
29.     msg:${sessionScope.msg}<br/>
30.     username:${sessionScope.users[1].name}<br/>
31.     <hr/>
32.     application域中的数据:<br/>
33.     msg:${applicationScope.msg}<br/>
34.     username:${applicationScope.userMap.a.name}<br/>
35.     <hr/>
36.     <%--EL表达式在取出数据的时候是可以省略域标志的
37.     EL表达式会自动依次到四个域中去找数据
38.     --%>
39.     PageContext username:${userx.name}<br/>
40.     Request username:${user.name}<br/>
41.     Session username:${users[1].name}<br/>
42.     Application username:${userMap.a.name}<br/>
43.     <hr/>
44.     <%--
45.     ${数据的名字}如果省略域标志,取数据的顺序如下
46.     pageContext
47.     request
48.     session
49.     application
50.     --%>
51.     ${msg}
52.     <hr/>
53.     <%--
54.     移除域中的数据
55.     --%>
56.     <%
57.          //pageContext.removeAttribute("msg");//
    pageContext.removeAttribute()方法会移除四个域中的所有的同名的数据
58.         //request.removeAttribute("msg");
59.     %>
60.     pagecontextMsg:${pageScope.msg}<br/>
61.     requestMsg:${requestScope.msg}<br/>
62.     sessionMsg:${sessionScope.msg}<br/>
63.     applicationMsg:${applicationScope.msg}<br/>
64.     <hr/>
65.     <%--
66.     EL表达式获取请求中的参数
67.     --%>
68.     username:${param.username}<br/>
69.     hobby:${paramValues.hobby[0]}
70.     hobby:${paramValues.hobby[1]}
71. </body>
72. </html>

 




 **总结:** 

EL表达式定义在JSP页面上,在转译之后的java文件中,会被转化成java代码 

EL表达式是一种后台技术,服务器上运行,不是在浏览器上运行,不能用于HTML页面 

EL表达式底层是通过反射实现的,在获取对象属性值时是通过对象的get方法实现的 




### EL表达式对运算符的支持 

在EL表达式中, 支持运算符的使用 

算数运算符: + - * / % 

比较运算符:  

==  eq equals 

>     gt greater then 

<     lt   lower then 

>=  ge  greater then or equals 

<=  le   lower then or equals 

!=   ne   not equals 

逻辑运算符: || or    && and  

三目运算符: ${条件 ?表达式1 : 表达式2} 

判空运算符: empty 

##### EL表达式运算符的使用   




1.  <%@ page import="java.util.List" %>
2.  <%@ page import="java.util.ArrayList" %>
3.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
4.  <html>
5.  <head>
6.      <title>Title</title>
7.  </head>
8.  <body>
9.  <%--
10. +两端如果有字符串,会尝试将字符串转换成数字之后进行加法运算
11. /如果除以0 结果为Infinity 而不是出现异常
12. %如果和0取余数,那么会出现异常
13. --%>
14.     算数运算符：
15.     <hr/>
16.     ${10 + 10}<br/>
17.     ${"10" + 10}<br/>
18.     ${"10" + "10"}<br/>
19.     <%--${"10a" + 10}<br/>--%>
20.     ${10/0}<br/>
21.     <%-- ${10%0}<br/>--%>
22.     关系运算符/比较运算符
23.     <%--
24.     比较运算符推荐写成字母形式,不推荐使用 == >=  <=
25.     --%>
26.     <hr/>
27.     ${10 == 10}<br/>
28.     ${10 eq 10}<br/>
29.     ${10 gt 8}<br/>
30.     逻辑运算符
31.     <hr/>
32.     ${ true || false}<br/>
33.     ${ true or false}<br/>
34.     ${ true && false}<br/>
35.     ${ true and false}<br/>
36.     条件运算符/三目运算符
37.     <hr/>
38.     ${(100-1)%3==0?10+1:10-1}<br/>
39.     判断空运算符
40.     <%--empty 为null 则为true--%>
41.     <%  //向域中放入数据
42.         pageContext.setAttribute("a",null);
43.         pageContext.setAttribute("b","");
44.         int[] arr ={};
45.         pageContext.setAttribute("arr",arr);
46.         List list =new ArrayList();
47.         pageContext.setAttribute("list",list);
48.     %>
49.     <hr/>
50.     ${empty a}<br/>
51.     ${empty b}<br/><%--字符串长度为0 则认为是空--%>
52.     ${empty arr}<br/><%--数组长度为0 认为不是空--%>
53.     ${empty list}<br/><%--集合长度为0 认为是空--%>
54.     ${list.size() eq 0}<br/><%--集合长度为0 认为是空--%>
55. </body>
56. </html>

 




使用EL表达式优化查询全部员工信息的页面处理 

1.  <%@ page import="java.util.List" %>
2.  <%@ page import="com.msb.pojo.Emp" %>
3.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
4.  <html>
5.  <head>
6.      <title>Title</title>
7.      <style>
8.          table{
9.              border: 3px solid blue;
10.             width: 80%;
11.             margin: 0px auto;
12.         }
13.         td,th{
14.             border: 2px solid green;
15.         }
16.     </style>
17. </head>
18. <body>
19.     <table cellspacing="0px" cellpadding="0px">
20.         <tr>
21.             <th>编号</th>
22.             <th>姓名</th>
23.             <th>上级编号</th>
24.             <th>职务</th>
25.             <th>入职日期</th>
26.             <th>薪资</th>
27.             <th>补助</th>
28.             <th>部门号</th>
29.             <th>薪资等级</th>
30.         </tr>
31.         <%
32.             List<Emp> emps = (List<Emp>) request.getAttribute("emps");
33.             for (Emp emp : emps) {
34.                 pageContext.setAttribute("emp", emp);//将员工对象放入PageContext 域
35.         %>
36.             <tr>
37.                 <td>${emp.empno}</td>
38.                 <td>${emp.ename}</td>
39.                 <td>${emp.mgr}</td>
40.                 <td>${emp.job}</td>
41.                 <td>${emp.hiredate}</td>
42.                 <td>${emp.sal}</td>
43.                 <td>${emp.comm}</td>
44.                 <td>${emp.deptno}</td>
45.                 <td>
46.                     ${emp.sal le 500?"A":""}
47.                     ${emp.sal gt 500 and emp.sal le 1000?"B":""}
48.                     ${emp.sal gt 1000 and emp.sal le 1500?"C":""}
49.                     ${emp.sal gt 1500 and emp.sal le 2000?"D":""}
50.                     ${emp.sal gt 2000 and emp.sal le 3000?"E":""}
51.                     ${emp.sal gt 3000 and emp.sal le 4000?"F":""}
52.                     ${emp.sal gt 4000?"G":""}
53.                 </td>
54.             </tr>
55.         <%
56.             }
57.         %>
58.     </table>
59. </body>
60. </html>






------------------------------------------------------------

