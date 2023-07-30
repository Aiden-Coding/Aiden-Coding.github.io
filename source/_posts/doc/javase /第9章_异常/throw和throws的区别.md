
# throw和throws的区别




1.  package com.msb.test01;
2.  import java.util.Scanner;
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test7 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) throws Exception {
9.          //实现一个功能：两个数相除，当除数为0的时候，程序出现异常。
10.         /*try {
11.             devide();
12.         } catch (Exception e) {
13.             e.printStackTrace();
14.         }*/
15.         devide();
16.     }
17.     public static void devide() throws Exception {
18.         Scanner sc = new Scanner(System.in);
19.         System.out.println("请录入第一个数：");
20.         int num1 = sc.nextInt();
21.         System.out.println("请录入第二个数：");
22.         int num2 = sc.nextInt();
23.         if(num2 == 0 ){//除数为0 ，制造异常。
24.             //制造运行时异常：
25.             /*throw new RuntimeException();*/
26.             //制造检查异常：
27.             /*try {
28.                 throw new Exception();
29.             } catch (Exception e) {
30.                 e.printStackTrace();
31.             }*/
32.             throw new Exception();
33.         }else{
34.             System.out.println("商："+num1/num2);
35.         }
36.     }
37. }

 




总结： 

throw和throws的区别： 

（1）位置不同： 

throw：方法内部 

throws: 方法的签名处，方法的声明处 




（2）内容不同： 

throw+异常对象（检查异常，运行时异常） 

throws+异常的类型（可以多个类型，用，拼接） 




（3）作用不同： 

throw：异常出现的源头，制造异常。 

throws:在方法的声明处，告诉方法的调用者，这个方法中可能会出现我声明的这些异常。然后调用者对这个异常进行处理： 

要么自己处理要么再继续向外抛出异常 
















































------------------------------------------------------------

