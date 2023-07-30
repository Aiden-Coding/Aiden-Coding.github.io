
# CSS的书写方式

【1】内联样式： 




1.  <!DOCTYPE html>
2.  <html>
3.          <head>
4.                  <meta charset="UTF-8">
5.                  <title></title>
6.          </head>
7.          <body>
8.                  <!--
9.                          书写方式：内联样式（行内样式）
10.                         在标签中加入一个style属性，CSS的样式作为属性值
11.                         多个属性值之间用;进行拼接
12.                 -->
13.                 <h1 style="color: deeppink;font-family: '宋体';">这是一个h1标题</h1>
14.         </body>
15. </html>

 

【2】内部样式： 




1.  <!DOCTYPE html>
2.  <html>
3.          <head>
4.                  <meta charset="UTF-8">
5.                  <title></title>
6.                  <!--
7.                          书写方式：内部样式：
8.                          head标签中加入一个style标签，在里面定位到你需要修饰的元素，然后在{}中加入你要修饰的样式。
9.                  -->
10.                 <style type="text/css">
11.                         h1{
12.                                 color: royalblue;
13.                                 font-family: 宋体;
14.                         }
15.                 </style>
16.         </head>
17.         <body>
18.                 <h1>这是一个标题</h1>
19.         </body>
20. </html>

 




【3】外部样式： 

首先要创建一个css文件，css文件的后缀.css 




1.  h1{
2.          color: red;
3.          font-family: 宋体;
4.  }

 

再创建html页面： 




1.  <!DOCTYPE html>
2.  <html>
3.          <head>
4.                  <meta charset="UTF-8">
5.                  <title></title>
6.                  <!--引入外部CSS资源：link-->
7.                  <link rel="stylesheet" type="text/css"
    href="css/mystyle.css"/>
8.          </head>
9.          <body>
10.                 <h1>这是一个标题</h1>
11.         </body>
12. </html> 




【4】实际开发中三种书写方式用的最多的是： 

第三种：外部样式：因为这种方式真正做到了  元素页面和样式 分离 




【5】三种书写方式优先级： 

就近原则 




1.  <!DOCTYPE html>
2.  <html>
3.          <head>
4.                  <meta charset="UTF-8">
5.                  <title></title>
6.                  <!--引入外部CSS资源：link-->
7.                  <style type="text/css">
8.                          h1{
9.                                  color: yellow;
10.                         }
11.                 </style>
12.                 <link rel="stylesheet" type="text/css"
    href="css/mystyle.css"/>
13.                 
14.         </head>
15.         <body>
16.                 <h1 style="color: red;">这是一个标题</h1>
17.         </body>
18. </html>

 















------------------------------------------------------------

