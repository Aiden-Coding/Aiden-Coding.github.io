
# 6_JSTL格式化标签

## JSTL格式化标签 

### 格式化标签库 

格式化标签库,也叫作fmt标签,是JTSL中的第二大组成部分,主要解决数据显示格式问题,让JSP页面的数据格式更加规范 

**格式化标签库导入的语句为:**   


|                                                                     |<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt"%>     |

  

fmt标签有如下属性：                                                                    
                                    


|                      |属性                    |                                |描述                              |         |是否必要     |                  |默认值               |
|----------------------|--------------------------------|---------|------------------|
|                      |value                 |                                |要显示的数字                          |         |是        |                  |无                 |
|                      |type                  |                                |NUMBER，CURRENCY，或 PERCENT类型     |         |否        |                  |Number            |
|                      |pattern               |                                |指定一个自定义的格式化模式用与输出               |         |否        |                  |无                 |
|                      |currencyCode          |                                |货币码（当type="currency"时）          |         |否        |                  |取决于默认区域           |
|                      |currencySymbol        |                                |货币符号 (当 type="currency"时)       |         |否        |                  |取决于默认区域           |
|                      |groupingUsed          |                                |是否对数字分组 (TRUE 或 FALSE)          |         |否        |                  |true              |
|                      |maxIntegerDigits      |                                |整型数最大的位数                        |         |否        |                  |无                 |
|                      |minIntegerDigits      |                                |整型数最小的位数                        |         |否        |                  |无                 |
|                      |maxFractionDigits     |                                |小数点后最大的位数                       |         |否        |                  |无                 |
|                      |minFractionDigits     |                                |小数点后最小的位数                       |         |否        |                  |无                 |
|                      |var                   |                                |存储格式化数字的变量                      |         |否        |                  |Print to page     |
|                      |scope                 |                                |var属性的作用域                       |         |否        |                  |page              |

如果type属性为percent或number，那么您就可以使用其它几个格式化数字属性。maxIntegerDigits属性和minIntegerDigits属性允许您指定整数的长度。若实际数字超过了
maxIntegerDigits所指定的最大值，则数字将会被截断。 

有一些属性允许您指定小数点后的位数。minFractionalDigits属性和maxFractionalDigits属性允许您指定小数点后的位数。若实际的数字超出了所指定的范围，则这个数字会被截断。
数字分组可以用来在每三个数字中插入一个逗号。groupingIsUsed属性用来指定是否使用数字分组。当与minIntegerDigits属性一同使用时，就必须要很小心地来获取预期的结果了。
您或许会使用pattern属性。这个属性可以让您在对数字编码时包含指定的字符。接下来的表格中列出了这些字符。                         
                           


|           |符号         |                                    |描述                                  |
|-----------|------------------------------------|
|           |0          |                                    |代表一位数字                              |
|           |E          |                                    |使用指数格式                              |
|           |#          |                                    |代表一位数字，若没有则显示 0，前导 0 和追尾 0 不显示。     |
|           |.          |                                    |小数点                                 |
|           |,          |                                    |数字分组分隔符                             |
|           |;          |                                    |分隔格式                                |
|           |-          |                                    |使用默认负数前缀                            |
|           |%          |                                    |百分数                                 |
|           |?          |                                    |千分数                                 |
|           |¤          |                                    |货币符号，使用实际的货币符号代替                    |
|           |X          |                                    |指定可以作为前缀或后缀的字符                      |
|           |&apos;     |                                    |在前缀或后缀中引用特殊字符                       |

### 日期格式化 

日期格式化标签是fmt标签中专门用于处理日期格式的标签 

<fmt:formatDate>标签有如下属性：                                                       
                 


|              |属性            |                                         |描述                                       |         |是否必要     |            |默认值         |
|--------------|-----------------------------------------|---------|------------|
|              |value         |                                         |要显示的日期                                   |         |是        |            |无           |
|              |type          |                                         |DATE, TIME, 或 BOTH                       |         |否        |            |date        |
|              |dateStyle     |                                         |FULL, LONG, MEDIUM, SHORT, 或 DEFAULT     |         |否        |            |default     |
|              |timeStyle     |                                         |FULL, LONG, MEDIUM, SHORT, 或 DEFAULT     |         |否        |            |default     |
|              |pattern       |                                         |自定义格式模式                                  |         |否        |            |无           |
|              |timeZone      |                                         |显示日期的时区                                  |         |否        |            |默认时区        |
|              |var           |                                         |存储格式化日期的变量名                              |         |否        |            |显示在页面       |
|              |scope         |                                         |存储格式化日志变量的范围                             |         |否        |            |页面          |

<fmt:formatDate>标签格式模式                                                         
                                                                     


|                 |代码               |                                             |描述                                           |                    |实例                  |
|-----------------|---------------------------------------------|--------------------|
|                 |G                |                                             |时代标志                                         |                    |AD                  |
|                 |y                |                                             |不包含纪元的年份。如果不包含纪元的年份小于 10，则显示不具有前导零的年份。       |                    |2002                |
|                 |M                |                                             |月份数字。一位数的月份没有前导零。                            |                    |April & 04          |
|                 |d                |                                             |月中的某一天。一位数的日期没有前导零。                          |                    |20                  |
|                 |h                |                                             |12 小时制的小时。一位数的小时数没有前导零。                      |                    |12                  |
|                 |H                |                                             |24 小时制的小时。一位数的小时数没有前导零。                      |                    |0                   |
|                 |m                |                                             |分钟。一位数的分钟数没有前导零。                             |                    |45                  |
|                 |s                |                                             |秒。一位数的秒数没有前导零。                               |                    |52                  |
|                 |S                |                                             |毫秒                                           |                    |970                 |
|                 |E                |                                             |周几                                           |                    |Tuesday             |
|                 |D                |                                             |一年中的第几天                                      |                    |180                 |
|                 |F                |                                             |一个月中的第几个周几                                   |                    |2 (一个月中的第二个星期三)     |
|                 |w                |                                             |一年中的第几周r                                     |                    |27                  |
|                 |W                |                                             |一个月中的第几周                                     |                    |2                   |
|                 |a                |                                             |a.m./p.m. 指示符                                |                    |PM                  |
|                 |k                |                                             |小时(12 小时制的小时)                                |                    |24                  |
|                 |K                |                                             |小时(24 小时制的小时)                                |                    |0                   |
|                 |z                |                                             |时区                                           |                    |中部标准时间              |
|                 |&apos;           |                                             |                                             |                    |转义文本                |
|                 |&apos;&apos;     |                                             |                                             |                    |单引号                 |

###  格式化标签案例开发 

##### 格式化标签处理页面数据显示格式 




1.  <%@ page contentType="text/html;charset=UTF-8" language="java" %>
2.  <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
3.  <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
4.  <html>
5.  <head>
6.      <title>Title</title>
7.      <style>
8.          table{
9.              border: 3px solid blue;
10.             width: 90%;
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
21.             <th>序号</th>
22.             <th>索引</th>
23.             <th>isFirst</th>
24.             <th>isLast</th>
25.             <th>工号</th>
26.             <th>姓名</th>
27.             <th>姓名</th>
28.             <th>上级编号</th>
29.             <th>职务</th>
30.             <th>入职日期</th>
31.             <th>薪资</th>
32.             <th>补助</th>
33.             <th>部门号</th>
34.             <th>薪资等级</th>
35.         </tr>
36.         <%--<%
37.         List<Emp> emps = (List<Emp>) request.getAttribute("emps");
38.         for (Emp emp : emps) {
39.             pageContext.setAttribute("emp", emp);//将员工对象放入PageContext 域
40.         %>
41.         c:foreach
42.             items 要遍历的数组/List  可以通过EL表达式取出集合之后给改属性赋值
43.             var   中间变量的名称
44.             varStatus 记录每一个对象状态的设置
45.                    count 个数
46.                    index 索引
47.                    first 如果当前元素是迭代的第一个元素 true 否则为false
48.                    last  如果当前元素是迭代的最后一个元素 true 否则为false
49.                    current 当前迭代的元素本身
50.         --%>
51.         <c:forEach items="${emps}" var="emp" varStatus="empStatus">
52.             <tr>
53.                 <td>${empStatus.count}</td>
54.                 <td>${empStatus.index}</td>
55.                 <td>${empStatus.first}</td>
56.                 <td>${empStatus.last}</td>
57.                 <td>${emp.empno}</td>
58.                 <td>${emp.ename}</td>
59.                 <td>${empStatus.current.ename}</td>
60.                 <td>${emp.mgr}</td>
61.                 <td>${emp.job}</td>
62.                 <td>
63.                     <fmt:formatDate value="${emp.hiredate}"
    pattern="yyyy年MM月dd日 HH:mm:ss"/>
64.                 </td>
65.                 <td>
66.                     <%--
67.                     0 代表必须有一位数字,如果对应的位置没有值怎么办?自动补充0
68.                     # 代表有一位数字,开头和结尾的所有的0不保留
69.                     --%>
70.                         &yen;<fmt:formatNumber value="${emp.sal}"
    pattern="###,##0.00"/>
71.                 </td>
72.                 <td>${emp.comm}</td>
73.                 <td>${emp.deptno}</td>
74.                 <td>
75.                    <c:choose>
76.                        <c:when test="${emp.sal le 500}">A</c:when>
77.                        <c:when test="${emp.sal le 1000}">B</c:when>
78.                        <c:when test="${emp.sal le 1500}">C</c:when>
79.                        <c:when test="${emp.sal le 2000}">D</c:when>
80.                        <c:when test="${emp.sal le 3000}">E</c:when>
81.                        <c:when test="${emp.sal le 4000}">F</c:when>
82.                        <c:when test="${emp.sal gt 4000}">G</c:when>
83.                    </c:choose>
84.                 </td>
85.             </tr>
86.         </c:forEach>
87.     </table>
88. </body>
89. </html>

 


 




------------------------------------------------------------

