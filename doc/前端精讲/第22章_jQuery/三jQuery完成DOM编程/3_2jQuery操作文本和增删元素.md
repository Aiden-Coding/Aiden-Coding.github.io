
# 3_2jQuery操作文本和增删元素

### jQuery操作文本和增删元素 

**操作文本** 

**原生js 中的通过元素.innerText和innerHTML和.value属性操作标签内部文本和内容,jQuery给我们封装了text(),html()和
val()三个方法** ** ** 

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  **         <head>**
4.  **                  <meta charset="utf-8">**
5.  **                  <title></title>**
6.  **                  <style>**
7.  **                          #d1{**
8.  **                                   width: 200px;**
9.  **                                   height: 200px;**
10. **                                   border: 1px solid green;**
11. **                          }**
12. **                  </style>**
13. **                  <script type="text/javascript" src="js/jquery.min.js"
    ></script>**
14. **                  <script>**
15. **                          function fun1(){**
16. **                          	/***
17. **                          	 * innerText >>>> text();**
18. **                          	 * innerHTML >>>> html();**
19. **                          	 * value     >>>> val();**
20. **                          	 * **
21. **                          	 * */**
22. **                             console.log($("#d1").text()) **
23. **                             console.log($("#d1").html())**
24. **                             console.log($("#i1").val())**
25. **                          }**
26. **                          function fun2(){**
27. **                          	//$("#d1").text("<h1>牛气冲天</h1>");**
28. **                          	$("#d1").html("<h1>牛气冲天</h1>");**
29. **                            $("#i1").val("你好");**
30. **                          }**
31. **                          function fun3(){**
32. **                            //$("#d1").html("");**
33. **                            $("#d1").empty();// 清空内容**
34. **                            $("#i1").val("");**
35. **                          }**
36. **                  </script>**
37. **         </head>**
38. **         <body>**
39. **                  <input type="text" value="这里是文字" id='i1' />**
40. **                  <div id='d1'>**
41. **                          a**
42. **                          <span>xxx</span>**
43. **                          b**
44. **                  </div>**
45. **                  <input  type="button" value="获得标签内容" onclick="fun1()"/>**
46. **                  <input  type="button" value="修改标签内容" onclick="fun2()"/>**
47. **                  <input  type="button" value="删除标签中的内容" onclick="fun3()"/>**
48. **         </body>**
49. **</html>** 




**增删元素** 

原生js 中的对于元素的创建,增加和删除代码比较繁琐,而jQuery从元素的创建到元素的增加和删除都给我们提供了更加便捷的方法 

创建元素 

$('<span>text<span>') 

追加元素 

append() appendTo() 添加内部标签 

before() insertBefore() 向前增加标签 

after() insertAfter()  向后增加标签 

删除元素 

empty()  清空字标签 

remove() 移除当前标签   

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  ** <head>**
4.  **          <meta charset="utf-8">**
5.  **          <title></title>**
6.  **          <style>**
7.  **                  #d1{**
8.  **                           width: 200px;**
9.  **                           height: 200px;**
10. **                           border: 1px solid red;**
11. **                           **
12. **                  }**
13. **          </style>**
14. **          <script type="text/javascript" src="js/jquery.min.js" ></script>**
15. **          <script>**
16. **                  function fun1(){**
17. **                  	  // 创建元素**
18. **                      var span1=$("<span></span>");**
19. **                      // 设置样式**
20. **                      span1.css("color","green");**
21. **                      span1.css("border","1px solid blue");**
22. **                      span1.css("background-color","lightgray")**
23. **                      // 设置文字**
24. **                      span1.text("今天天气很好");**
25. **                      **
26. **                      **
27. **                      $('#d1').append(span1)**
28. **                      **
29. **                  }**
30. **                  function fun2(){**
31. **                      var h
    =$("<h3>测试文字</h3>").css("color","red").css("border","1px solid green")**
32. **                      h.appendTo($('#d1'))**
33. **                  }**
34. **                  function fun3(){**
35. **                      var span1=$('<span style="color: red; border: 1px
    solid orangered;">测试文字</span>') **
36. **                      $("#d1").before(span1);**
37. **                  }**
38. **                  function fun4(){**
39. **                      var span1=$('<span style="color: red; border: 1px
    solid orangered;">测试文字</span>') **
40. **                      span1.insertBefore($("#d1"));**
41. **                  }**
42. **                  function fun5(){**
43. **                      var span1=$('<span style="color: red; border: 1px
    solid orangered;">测试文字</span>') **
44. **                      $("#d1").after(span1);**
45. **                  }**
46. **                  function fun6(){**
47. **                      var span1=$('<span style="color: red; border: 1px
    solid orangered;">测试文字</span>') **
48. **                      span1.insertAfter($("#d1"));**
49. **                  }**
50. **                  function fun7(){**
51. **                      $("#d1").empty()**
52. **                  }**
53. **                  function fun8(){**
54. **                  	 $("#d1").remove(); // 移除当前元素本身**
55. **                  }**
56. **          </script>**
57. ** </head>**
58. ** <body>**
59. ** 	**
60. ** 	**
61. **          <div id='d1'>**
62. **          	**
63. **          </div>**
64. **          <input type="button" value="testAppend" onclick="fun1()" />**
65. **          <input type="button" value="testAppendTo" onclick="fun2()" />**
66. **          <input type="button" value="testbefore" onclick="fun3()" />**
67. **          <input type="button" value="testinsertBefore" onclick="fun4()" />**
68. **          <input type="button" value="testafter" onclick="fun5()" />**
69. **          <input type="button" value="testInsertAfter" onclick="fun6()" />**
70. **          <input type="button" value="empty" onclick="fun7()" />**
71. **          <input type="button" value="remove" onclick="fun8()" />**
72. ** </body>**
73. **</html>**






------------------------------------------------------------

