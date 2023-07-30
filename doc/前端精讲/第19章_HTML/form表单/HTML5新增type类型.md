
# HTML5新增type类型

html5版本新增了很多类型，我们挑一些常用的进行展示： 

详细学习地址可以参照w3c进行学习： 

https://www.w3school.com.cn/html5/att_input_type.asp 




1.  <!DOCTYPE html>
2.  <html>
3.          <head>
4.                  <meta charset="UTF-8">
5.                  <title></title>
6.          </head>
7.          <body>
8.                  <form action="" method="get">
9.                          <!--email:
10.                                 html5的类型可以增加校验
11.                         -->
12.                         <input type="email" name="email" />
13.                         <!--url-->
14.                         <input type="url" />
15.                         <!--color-->
16.                         <input type="color" />
17.                         <!--number:
18.                                 min:最小值
19.                                 max:最大值
20.                                 step:步长
21.                                 value:默认值：一定在步长的范围中，否则不能提交
22.                         -->
23.                         <input type="number" min="1" max="10" step="3"
    value="4"/>
24.                         <!--range-->
25.                         1<input type="range" min="1" max="10" name="range"
    step="3"/>10
26.                         <!--date-->
27.                         <input type="date" />
28.                         <!--month-->
29.                         <input type="month" />
30.                         <!--week-->
31.                         <input type="week" />
32.                         <!--提交按钮-->
33.                         <input type="submit" />
34.                 </form>
35.         </body>
36. </html>

 






------------------------------------------------------------

