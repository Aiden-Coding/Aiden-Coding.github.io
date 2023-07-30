
# 3_3jQuery绑定和触发事件

###  jQuery操作事件 

**操作事件** 

无非就是绑定事件,触发事件,解绑定事件.原生js中的通过DOM编程和在标签上的事件属性绑定事件, 

jQuery中,我们可以使用 

事件的绑定:bind(),live()(1.8及之前可用),on()(1.9之后推荐使用),one() 

事件解绑定:unbind() 

事件的触发:行为触发, jQuery方法触发 




1.  <!DOCTYPE html>
2.  <html>
3.      <head>
4.           <meta charset="UTF-8">
5.           <title></title>
6.           <style>
7.               #d1{
8.                    width: 200px;
9.                    height: 200px;
10.                   border: 1px solid red;
11.              }
12.          </style>
13.          <script type="text/javascript"   src="js/jquery.min.js"  
    ></script>
14.          <script>
15.              function fun1(){
16.                 //给元素绑定事件
17.                 //原生JS
18.                 /*var div1=document.getElementById("d1")
19.                 div1.onmouseover=function (){
20.                 	alert("悬停")
21.                 }*/
22.                
23.                
24.                /* bind 方法绑定事件
25.                 * 在jQuery中,事件的名称= 原始名称去掉 on
26.                 * onclick       click
27.                 * onmouseover   mouseover
28.                 * 
29.                 * */
30.                 $("#d1").bind('mouseover',function(){
31.                 	$('#d1').css("background-color",'yellow')
32.                 });
33.                 
34.                 /*事件名作为方法*/
35.                 $("#d1").mouseleave(function(){
36.                 	$('#d1').css("background-color",'lightgreen')
37.                 });
38.                 
39.                 
40.                 /*
41.                  * one 绑定事件一次 
42.                  * 
43.                  * */
44.                 /*$("#d1").one('mouseover',function(){
45.                 	$('#d1').css("background-color",'yellow')
46.                 });
47.                 
48.                  $("#d1").one('mouseleave',function(){
49.                 	$('#d1').css("background-color",'lightgreen')
50.                 });*/
51.                
52.                 
53.              }
54.              function fun2(){
55.              	//$("#d1").unbind();  接触绑定的所有事件
56.              	$("#d1").unbind("mouseover") // 接触绑定的指定事件
57.                  
58.              }
59.              function fun3(){
60.                  // 相当于发生了获得焦点事件
61.                  $("#i1").focus()
62.              }
63.              function fun4(){
64.                  console.log("获得焦点了")
65.              }
66.          </script>
67.     </head>
68.     <body>
69.          <div id='d1'>
70.          	
71.          </div>
72.          <input type="button"   value="添加事件" onclick="fun1()" />
73.          <input type="button"   value="解除绑定" onclick="fun2()" />
74.          <br />
75.          <input type="text"  id='i1' onfocus="fun4()"/>
76.          <input type="button"   value="触发事件" onclick="fun3()" />
77.     </body>
78. </html>

 






------------------------------------------------------------

