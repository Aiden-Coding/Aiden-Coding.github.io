
# 5_JSTL核心标签库

## JSTL核心标签 

### 认识JSTL 

**为什么需要学习JSTL** 

通过之前的案例我们发现,就算在JSP中可以使用EL表达式取出域对象中的数据,但是仍然避免不了还是要在页面中书写一些java代码.这种嵌入JAVA代码的处理比较繁琐
,容易出错,且代码不容易维护. 

**什么是JSTL** 

JSTL（Java server pages standarded tag library，即JSP标准标签库）是由
[JCP](https://baike.baidu.com/item/JCP/2679009)（Java community Proces）所制定的标准规范，它主要提供给
Java Web开发人员一个标准通用的标签库，并由Apache的Jakarta小组来维护。 

**使用JSTL的好处:** 

开发人员可以利用JSTL和EL来开发Web程序，取代传统直接在页面上嵌入Java程序的做法，以提高程序的阅读性、维护性和方便性。在jstl中, 提供了多套标签库
, 用于方便在jsp中完成或简化相关操作. 

**JSTL标签库的组成部分 **

>核心标签库: core, 简称c 

>格式化标签库: format, 简称fmt 

>函数标签库: function, 简称fn 

**JSTL的使用前提** 

1需要在项目中导入jstl-1.2.jar ,jstl在后台由java代码编写, jsp页面中通过标签进行使用, 使用标签时, 会自动调用后台的java方法, 

2标签和方法之间的映射关系在对应的tld文件中描述. 需要在页面中通过taglib指令引入对应的标签库, uri可以在对应的tld文件中找到   


|                                                 |<%@   taglib uri="标签库的定位" prefix="前缀(简称)" %>     |

**核心标签库导入的语句为:**   


|                                                                    |<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>     |

### 操作域对象的标签: 

<c:set>         向域对象中放入数据  setAttribute 

<c:out>        从域对象中取出数据  getAttribute 

<c:remove> 从域对象中移除数据   removeAttribute 

##### c:set/out/remove标签的使用 




1.  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
2.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
3.  <html>
4.  <head>
5.      <title>Title</title>
6.  </head>
7.  <body>
8.      <%--分别向四个域中放入数据--%>
9.      <%--<%
10.     request.setAttribute("msg", "requestMessage");
11.     %>--%>
12.     <%--
13.     c:set
14.         scope 指定放数据的域 可选值 page request session application
15.         var   数据的名称
16.         value 数据
17.     --%>
18.     <c:set scope="page" var="msg" value="pageMessage"></c:set>
19.     <c:set scope="request" var="msg" value="requestMessage"></c:set>
20.     <c:set scope="session" var="msg" value="sessionMessage"></c:set>
21.     <c:set scope="application" var="msg" value="applicationMessage"></c:set>
22.     <%--移除指定域中的值--%>
23.    <%-- <c:remove var="msg" scope="page"></c:remove>
24.     <c:remove var="msg" scope="request"></c:remove>--%>
25.     <c:remove var="msg" scope="session"></c:remove>
26.     <c:remove var="msg" scope="application"></c:remove>
27.     <%--通过EL表达式取出域中的值--%>
28.     <hr/>
29.     ${pageScope.msg}<br/>
30.     ${requestScope.msg}<br/>
31.     ${sessionScope.msg}<br/>
32.     ${applicationScope.msg }<br/>
33.     <hr/>
34.     <%--通过c:out标签获取域中的值--%>
35.     <c:out value="${pageScope.msg}" default="page msg not found"/>
36.     <c:out value="${requestScope.msg}" default="request msg not found"/>
37.     <c:out value="${sessionScope.msg}" default="session msg not found"/>
38.     <c:out value="${applicationScope.msg}" default="application msg not
    found"/>
39. </body>
40. </html>

 




### 多条件分支标签 

##### c:if和c:choose标签的使用   




1.  <%@ page import="java.util.Random" %>
2.  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
3.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
4.  <html>
5.  <head>
6.      <title>Title</title>
7.  </head>
8.  <body>
9.      <%--
10.     随机生成一个分数  0-100
11.     >=90 A
12.     >=80 B
13.     >=70 C
14.     >=60 D
15.     <60  E
16.     --%>
17.     <%
18.         int score =new Random().nextInt(101);
19.         pageContext.setAttribute("score", score);
20.     %>
21.     <%--
22.     test  判断条件
23.     c:if可以将test的结果放入指定的域中
24.     scope 指定存放的域
25.     var   数据名
26.     --%>
27.     分数:${score}<br/> 等级:
28.     <c:if test="${score ge 90}" scope="page" var="f1">A</c:if>
29.     <c:if test="${score ge 80 and score lt 90}" scope="page"
    var="f2">B</c:if>
30.     <c:if test="${score ge 70 and score lt 80}" scope="page"
    var="f3">C</c:if>
31.     <c:if test="${score ge 60 and score lt 70}" scope="page"
    var="f4">D</c:if>
32.     <c:if test="${score lt 60}" scope="page" var="f5">E</c:if>
33.     <hr/>
34.     ${f1}
35.     ${f2}
36.     ${f3}
37.     ${f4}
38.     ${f5}
39.     <hr/>
40.     <%--输出分数是否及格--%>
41.     <c:if test="${score ge 60}" scope="page" var="flag">及格</c:if>
42.     <c:if test="${!pageScope.flag}">不及格</c:if>
43.     <hr/>
44.     <c:choose>
45.         <c:when test="${score ge 90}">A</c:when>
46.         <c:when test="${score ge 80}">B</c:when>
47.         <c:when test="${score ge 70}">C</c:when>
48.         <c:when test="${score ge 60}">D</c:when>
49.         <c:otherwise>E</c:otherwise>
50.     </c:choose>
51. </body>
52. </html>

 




### 迭代标签 

##### c:foreach打印99乘法表 

c:forEach中的属性 

> var: 迭代变量, 存放在pageContext作用域 

> begin: 迭代起始值 

> end: 迭代结束值 

> step: 迭代变量变化的步长   




1.  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
2.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
3.  <html>
4.  <head>
5.      <title>Title</title>
6.  </head>
7.  <body>
8.      <%--
9.      for ( int i =1;i<=9 ;i+=2){
10.         pageContext.setAttribute("i",i)
11.     }
12.     c:foreach 每次执时都会向page域中放入一个名为 i 值为当前值这样的一个操作
13.     --%>
14.     <c:forEach var="i" begin="1" end="9" step="1">
15.         <c:forEach var="j" begin="1" end="${i}" step="1">
16.             ${j} * ${i} = ${i*j} &nbsp;
17.         </c:forEach>
18.         <br/>
19.     </c:forEach>
20. </body>
21. </html>

 




##### c:foreach遍历对象数组/List 

  items: 要遍历的集合, 需要使用EL表达式取值 

varStatus: 迭代变量的状态 

index: 索引, 从0开始 

count: 计数, 从1开始 

first: boolean, 表示是否是第一个 

last: boolean, 表示是否是最后一个 

current: 对象, 当前迭代的对象值 

后台代码   




1.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
2.  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
3.  <html>
4.  <head>
5.      <title>Title</title>
6.      <style>
7.          table{
8.              border: 3px solid blue;
9.              width: 90%;
10.             margin: 0px auto;
11.         }
12.         td,th{
13.             border: 2px solid green;
14.         }
15.     </style>
16. </head>
17. <body>
18.     <table cellspacing="0px" cellpadding="0px">
19.         <tr>
20.             <th>序号</th>
21.             <th>索引</th>
22.             <th>isFirst</th>
23.             <th>isLast</th>
24.             <th>工号</th>
25.             <th>姓名</th>
26.             <th>姓名</th>
27.             <th>上级编号</th>
28.             <th>职务</th>
29.             <th>入职日期</th>
30.             <th>薪资</th>
31.             <th>补助</th>
32.             <th>部门号</th>
33.             <th>薪资等级</th>
34.         </tr>
35.         <%--<%
36.         List<Emp> emps = (List<Emp>) request.getAttribute("emps");
37.         for (Emp emp : emps) {
38.             pageContext.setAttribute("emp", emp);//将员工对象放入PageContext 域
39.         %>
40.         c:foreach
41.             items 要遍历的数组/List  可以通过EL表达式取出集合之后给改属性赋值
42.             var   中间变量的名称
43.             varStatus 记录每一个对象状态的设置
44.                    count 个数
45.                    index 索引
46.                    first 如果当前元素是迭代的第一个元素 true 否则为false
47.                    last  如果当前元素是迭代的最后一个元素 true 否则为false
48.                    current 当前迭代的元素本身
49.         --%>
50.         <c:forEach items="${emps}" var="emp" varStatus="empStatus">
51.             <tr>
52.                 <td>${empStatus.count}</td>
53.                 <td>${empStatus.index}</td>
54.                 <td>${empStatus.first}</td>
55.                 <td>${empStatus.last}</td>
56.                 <td>${emp.empno}</td>
57.                 <td>${emp.ename}</td>
58.                 <td>${empStatus.current.ename}</td>
59.                 <td>${emp.mgr}</td>
60.                 <td>${emp.job}</td>
61.                 <td>${emp.hiredate}</td>
62.                 <td>${emp.sal}</td>
63.                 <td>${emp.comm}</td>
64.                 <td>${emp.deptno}</td>
65.                 <td>
66.                    <c:choose>
67.                        <c:when test="${emp.sal le 500}">A</c:when>
68.                        <c:when test="${emp.sal le 1000}">B</c:when>
69.                        <c:when test="${emp.sal le 1500}">C</c:when>
70.                        <c:when test="${emp.sal le 2000}">D</c:when>
71.                        <c:when test="${emp.sal le 3000}">E</c:when>
72.                        <c:when test="${emp.sal le 4000}">F</c:when>
73.                        <c:when test="${emp.sal gt 4000}">G</c:when>
74.                    </c:choose>
75.                 </td>
76.             </tr>
77.         </c:forEach>
78.     </table>
79. </body>
80. </html>

 







  



------------------------------------------------------------

