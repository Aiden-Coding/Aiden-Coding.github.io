
# 通过if-else解决异常




1.  package com.msb.test01;
2.  import java.util.Scanner;
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //实现一个功能：键盘录入两个数，求商：
10.         Scanner sc = new Scanner(System.in);
11.         System.out.println("请录入第一个数：");
12.         if(sc.hasNextInt()){
13.             int num1 = sc.nextInt();
14.             System.out.println("请录入第二个数：");
15.             if(sc.hasNextInt()){
16.                 int num2 = sc.nextInt();
17.                 if(num2 == 0){
18.                     System.out.println("对不起，除数不能为0");
19.                 }else{
20.                     System.out.println("商："+num1/num2);
21.                 }
22.             }else{
23.                 System.out.println("对不起，你录入的不是int类型的数据！");
24.             }
25.         }else{
26.             System.out.println("对不起，你录入的不是int类型的数据！");
27.         }
28.     }
29. }

 

用if-else堵漏洞的缺点： 

（1）代码臃肿，业务代码和处理异常的代码混在一起。 

（2）可读性差 

（3）程序员需要花费大量的经历来维护这个漏洞 

（4）程序员很难堵住所有的漏洞。 












------------------------------------------------------------

