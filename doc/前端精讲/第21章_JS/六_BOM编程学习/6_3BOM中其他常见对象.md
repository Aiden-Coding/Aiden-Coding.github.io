
# 6_3BOM中其他常见对象

#### location对象 

location对象,是window对象的一个属性,代表浏览器上URL地址栏,使用location对象可以操作地址栏   

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  **        <head>**
4.  **                <meta charset="UTF-8">**
5.  **                <title></title>**
6.  **                <script>**
7.  **                        function fun1(){**
8.  **                                console.log(location.host);// 服务器的IP+端口号**
9.  **                                console.log(location.hostname);// IP **
10. **                                console.log(location.port);// 端口号**
11. **                                console.log(location.href);// 地址栏中具体的文字**
12. **                        **
13. **                                location.href="https://www.baidu.com"**
14. **                        }**
15. **                        **
16. **                </script>**
17. **        </head>**
18. **        <body>**
19. **                <input type="button" value="测试location" onclick="fun1()" />**
20. **        </body>**
21. **</html>**

 




#### history对象 

history对象是window对象的一个属性,代表浏览器访问历史记录,通过history的操作我们可以实现翻阅浏览器历史网页 

  

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  **        <head>**
4.  **                <meta charset="UTF-8">**
5.  **                <title></title>**
6.  **                <script>**
7.  **                        function fun1(){**
8.  **                                window.history.forward();**
9.  **                                **
10. **                        }**
11. **                        function fun2(){**
12. **                                history.back();**
13. **                        }**
14. **                        function fun3(){**
15. **                                history.go(2); // 正整数 向前跳转 * 页  负整数 向后跳转*页**
16. **                        }**
17. **        **
18. **                        **
19. **                </script>**
20. **        </head>**
21. **        <body>**
22. **                <a href="a.html" target="_self">pageA</a>**
23. **                <input type="button" value="向前" onclick="fun1()"/>**
24. **                <input type="button" value="向后" onclick="fun2()"/>**
25. **                <input type="button" value="go" onclick="fun3()"/>**
26. **        </body>**
27. **</html>**

 

**screen和navigator** 

screen代表屏幕,navigator代表浏览器软件本身,通过这两个对象可以获得屏幕和浏览器软件的一些信息   

**
**

1.  **<!DOCTYPE html>**
2.  **<html>**
3.  **        <head>**
4.  **                <meta charset="UTF-8">**
5.  **                <title></title>**
6.  **                <script>**
7.  **                        function fun1(){**
8.  **                                console.info(window.screen.width)**
9.  **                                console.info(window.screen.height)**
10. **                                console.info(navigator.userAgent)**
11. **                                console.info(navigator.appName)**
12. **                        }**
13. **                </script>**
14. **        </head>**
15. **        <body onload="fun1()">**
16. **        </body>**
17. **</html>**

 

**
**

                        



------------------------------------------------------------

