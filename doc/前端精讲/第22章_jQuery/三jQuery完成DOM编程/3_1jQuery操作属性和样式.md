
# 3_1jQuery操作属性和样式

### jQuery操作属性和样式 

**操作属性** 

原生js 中的通过元素.属性名或者元素.setAttribute()方式操作元素属性,jQuery给我们封装了attr() 和removeAttr(),更加便捷的操作属性
     




1.  <!DOCTYPE html>
2.  <html>
3.      <head>
4.           <meta charset="UTF-8">
5.           <title></title>
6.           <style>
7.               .a{
8.                    background-color: aqua;
9.               }
10.          </style>
11.          <script type="text/javascript"   src="js/jquery.min.js"  
    ></script>
12.          <script>
13.          	/*
14.          	 *attr() 
15.          	 * 
16.          	 * */
17.              function fun1(){
18.                   console.log($("#f1").attr("color"))
19.                   console.log($("#f1").attr("id"))
20.                   console.log($("#f1").attr("size"))
21.              }
22.              function fun2(){
23.                  $("#f1").attr("color","green")
24.                  $("#f1").attr("size","5")
25.              }
26.              function fun3(){
27.                  $("#f1").removeAttr("color") 
28.              }
29.              function fun4(){
30.                 $("#f1").attr("class","a")
31.              }
32.          </script>
33.     </head>
34.     <body>
35.          <font id='f1' color="red" size="7" >牛气冲天</font>
36.          <hr />
37.          <input type="button"   value="获得属性" onclick="fun1()" />
38.          <input type="button"   value="修改属性" onclick="fun2()" />
39.          <input type="button"   value="删除属性" onclick="fun3()" />
40.          <input type="button"   value="添加属性" onclick="fun4()" />
41.     </body>
42. </html>




 



**操作样式** 

原生js 中的通过元素.style.样式名=’样式值’的方式操作元素样式,jQuery给我们封装了css()方法,便于我们操作样式,多数情况样式选择器使用类选择器
,所以jQuery针对于这一情况,给我们封装了addClass  removeClass toggleClass 三个方法      







1.  <!DOCTYPE html>
2.  <html>
3.      <head>
4.           <meta charset="UTF-8">
5.           <title></title>
6.           <style>
7.            .a{
8.                width: 100px;
9.                height: 100px;
10.               background-color: pink;
11.           }  
12.           .b{
13.               border: 10px solid green;
14.               border-radius: 20px;
15.           }
16.          </style>
17.          <script type="text/javascript"   src="js/jquery.min.js"  
    ></script>
18.          <!--
19.          	元素.style.样式名=
20.          	css()
21.          -->
22.          <script>
23.              function fun1(){
24.                  //获得d1的css样式
25.                  console.log($("#d1").css("width"));
26.                  console.log($("#d1").css("height"));
27.                  console.log($("#d1").css("background-color"));
28.                  //修改d1的css样式
29.                  
30.                  $("#d1").css("width","200px")
31.                  $("#d1").css("height","300px")
32.                  $("#d1").css("background-color","yellow");
33.              }
34.              /*
35.               * CSS 样式在实际的研发中,往往通过类选择器作用到元素上
36.               * jQuery就专门的封装了操作class属性值的方法
37.               * */
38.            
39.              function fun2(){
40.                 $("#d2").addClass("b")
41.              }
42.              function fun3(){
43.                 $("#d2").removeClass("b")
44.              }
45.              function fun4(){
46.                 $("#d2").toggleClass("b")// 原来有b 则删除,如果没有,则增加b
47.              }
48.          </script>
49.     </head>
50.     <body>
51.          <div id="d1"class="a">
52.          </div>
53.          <input type="button"   value="修改样式" onclick="fun1()" />
54.          <div id="d2"  class="a" >
55.              d2
56.          </div>
57.          <input type="button"   value="添加class值" onclick="fun2()" />
58.          <input type="button"   value="删除class值" onclick="fun3()" />
59.          <input type="button"   value="切换class值" onclick="fun4()" />
60.     </body>
61. </html>

 



























------------------------------------------------------------

