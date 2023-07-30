
# 3_4DOM对象和jQuery对象转换

### jQuery对象和DOM对象的转换 

使用原生JS方式获得的页面结点对象我们可以简称为DOM对象,使用jQuery核心函数获得的对象我们可以简称为jQuery对象,这两种方式获得的对象即是是页面上同一个元素
,那么也是不一样的,二者之间的API是不通用的.而在某些情况下,我们往往无法选择接收的对象,只能被动使用,那么这个时候我们可以让二者实现转换,以达到可以调用API
实现功能的目的 

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  **        <head>**
4.  **                <meta charset="utf-8">**
5.  **                <title></title>**
6.  **                <script type="text/javascript" src="js/jquery.min.js"
    ></script>**
7.  **                <script>**
8.  **                        $(function(){**
9.  **                                //1 原生JS获取页面元素  原生DOM对象**
10. **                                var div1=document.getElementById("d1");**
11. **                                **
12. **                                //2 jQuery方式获取页面元素 jQuery对象**
13. **                                var div2=$("#d1");**
14. **                                /***
15. **                                 * DOM对象和jQuery对象之间的方法和属性是不通用**
16. **                                 *  **
17. **                                 * */**
18. **                                console.log(div1.innerText);**
19. **                                console.log(div2.text());**
20. **                                **
21. **                                console.log(div1)**
22. **                                console.log(div2)**
23. **                                **
24. **                                **
25. **                                // DOM对象如何调用jQuery函数  DOM对象转换为jQuery   
    $(DOM)**
26. **                                console.log($(div1).text());**
27. **                                // jQuery对象如何调用DOM对象的属性和方法   jQuery转换为DOM对象
     get(0)  [0]**
28. **                                console.log(div2.get(0).innerText)**
29. **                                console.log(div2[0].innerText)**
30. **                                **
31. **                        })**
32. **                        **
33. **                        **
34. **                </script>**
35. **                **
36. **        </head>**
37. **        <body>**
38. **                <div id="d1">测试文字</div>**
39. **        </body>**
40. **</html>** 




注意: 

使用原生JSDOM对象转换成jQuery对象方式是$(dom对象),jQuery对象转换成DOM对象的方式是jQuery对象[0]/.get(0) 



------------------------------------------------------------

