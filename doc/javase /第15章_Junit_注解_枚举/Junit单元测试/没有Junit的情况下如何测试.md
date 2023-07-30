
# 没有Junit的情况下如何测试

在没有使用Junit的时候，缺点： 

（1）测试一定走main方法，是程序的入口，main方法的格式必须不能写错。 

（2）要是在同一个main方法中测试的话，那么不需要测试的东西必须注释掉。 

（3）测试逻辑如果分开的话，需要定义多个测试类，麻烦。 

（4）业务逻辑和测试代码，都混淆了。 

代码： 




1.  package com.msb.calculator;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Calculator {
6.      //加法：
7.      public int add(int a,int b){
8.          return a+b;
9.      }
10.     //减法：
11.     public int sub(int a,int b){
12.         return a-b;
13.     }
14. }

 




1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //测试加法：
5.          Calculator cal = new Calculator();
6.          int result = cal.add(10, 20);
7.          System.out.println(result);
8.          //测试减法：
9.         /* int result = cal.sub(30, 10);
10.         System.out.println(result);*/
11.     }
12. } 




1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          Calculator cal = new Calculator();
5.          //测试减法：
6.          int result = cal.sub(30, 10);
7.          System.out.println(result);
8.      }
9.  }

 






------------------------------------------------------------

