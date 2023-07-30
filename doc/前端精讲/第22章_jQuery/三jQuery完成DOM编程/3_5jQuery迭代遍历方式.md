
# 3_5jQuery迭代遍历方式

### jQuery中的迭代遍历方式   

jQuery给我们封装了一个快捷遍历元素的方法,接下来我们就使用一下jQuery中新的遍历方式 




1.  <!DOCTYPE html>
2.  <html>
3.      <head>
4.           <meta charset="utf-8">
5.           <title></title>
6.           <script type="text/javascript" src="js/jquery.min.js" ></script>
7.           <script>
8.               $(function(){
9.                    var $lis =$('li')
10.                   console.info($lis)
11.                   for(var i = 0;i<$lis.length;i++){
12.                       /*遍历出的每个元素是DOM对象*/
13.                       console.info($lis[i].innerText)
14.                   }
15.                   for(var i in $lis){
16.                       console.info($lis[i].innerText)
17.                   }
18.                   /*遍历所有元素的方法*/
19.                   /*
20.                    each每拿出一个元素 都会执行一次内部的function
21.                    i 当前元素的所有
22.                    e 当前元素 DOM对象
23.                    *
24.                    * */
25.                   $lis.each(function (i,e){
26.                       console.info(i+'>>>'+$(e).text())
27.                   })
28.                   $.each($lis,function (i,e){
29.                       console.info(i+'>>>'+$(e).text())
30.                   })
31.              })
32.          </script>
33.     </head>
34.     <body>
35.          <ul>
36.              <li>AI</li>
37.              <li>Python</li>
38.              <li>大数据</li>
39.              <li>JAVA</li>
40.              <li>前端</li>
41.          </ul>
42.     </body>
43. </html>

 


     


  



------------------------------------------------------------

