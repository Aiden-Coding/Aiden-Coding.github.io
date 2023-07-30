
# @Before_@After

@Before: 

某一个方法中，加入了@Before注解以后，那么这个方法中的功能会在测试方法执行前先执行 

一般会在@Beforer修饰的那个方法中加入：加入一些申请资源的代码：申请数据库资源，申请IO资源，申请网络资源。。。 







@After: 

某一个方法中，加入了@After注解以后，那么这个方法中的功能会在测试方法执行后先执行 

一般会在@After修饰的那个方法中加入：加入释放资源的代码：释放数据库资源，释放IO资源，释放网络资源。。。 




代码： 




1.  package com.msb.test;
2.  import com.msb.calculator.Calculator;
3.  import org.junit.After;
4.  import org.junit.Assert;
5.  import org.junit.Before;
6.  import org.junit.Test;
7.  /**
8.   * @Auther: msb-zhaoss
9.   */
10. public class CalculatorTest {
11.     @Before
12.     public void init(){
13.         System.out.println("方法执行开始了。。。");
14.     }
15.     @After
16.     public void close(){
17.         System.out.println("方法执行结束了。。。");
18.     }
19.     //测试add方法
20.     @Test
21.     public void testAdd(){
22.         System.out.println("测试add方法");
23.         Calculator cal = new Calculator();
24.         int result = cal.add(10, 30);
25.         //System.out.println(result);--》程序的运行结果可以不关注
26.         //加入断言：预测一下结果，判断一下我预测的结果和 实际的结果是否一致：
27.         Assert.assertEquals(40,result);//第一个参数：预测结果  第二个参数：实际结果
28.     }
29.     //测试sub方法
30.     @Test
31.     public void testSub(){
32.         System.out.println("测试sub方法");
33.         Calculator cal = new Calculator();
34.         int result = cal.sub(10, 30);
35.         System.out.println(result);
36.     }
37. }

 






------------------------------------------------------------

