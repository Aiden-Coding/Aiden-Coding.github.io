
# Junit的注解

@Test 

@Before 

@After 




代码： 




1.  package com.msb.test;
2.  import com.msb.calculator.Calculator;
3.  import org.junit.After;
4.  import org.junit.Assert;
5.  import org.junit.Before;
6.  import org.junit.Test;
7.  public class CalculatorTest {
8.      @Before
9.      public void init(){
10.         System.out.println("方法执行开始了。。。");
11.     }
12.     @After
13.     public void close(){
14.         System.out.println("方法执行结束了。。。");
15.     }
16.     @Test
17.     public void testAdd(){
18.         System.out.println("测试add方法");
19.         Calculator cal = new Calculator();
20.         int result = cal.add(10, 30);
21.         Assert.assertEquals(40,result);//第一个参数：预测结果  第二个参数：实际结果
22.     }
23. }

 






------------------------------------------------------------

