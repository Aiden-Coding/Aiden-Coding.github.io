
# try-catch-finally

【1】在什么情况下，try-catch后面的代码不执行？ 

（1）throw抛出异常的情况 

（2）catch中没有正常的进行异常捕获 

（3）在try中遇到return 




【2】怎么样才可以将 try-catch后面的代码  必须执行？ 

只要将必须执行的代码放入finally中，那么这个代码无论如何一定执行。 




【3】return和finally执行顺序？ 

先执行finally最后执行return 




【4】什么代码会放在finally中呢？ 

关闭数据库资源，关闭IO流资源，关闭socket资源。 




【5】有一句话代码很厉害，它可以让finally中代码不执行! 

[System.exit(0);//终止当前的虚拟机执行](System.exit(0);//终止当前的虚拟机执行) 







代码： 




1.  package com.msb.test01;
2.  import java.util.Scanner;
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test3 {
7.      public static void main(String[] args) {
8.          //实现一个功能：键盘录入两个数，求商：
9.          try{
10.             Scanner sc = new Scanner(System.in);
11.             System.out.println("请录入第一个数：");
12.             int num1 = sc.nextInt();
13.             System.out.println("请录入第二个数：");
14.             int num2 = sc.nextInt();
15.             System.out.println("商："+num1/num2);
16.             System.exit(0);//终止当前的虚拟机执行
17.             return;
18.         }catch(ArithmeticException ex){
19.             //throw ex;
20.         }finally {
21.             System.out.println("----谢谢你使用计算器111");
22.         }
23.     }
24. }

 






------------------------------------------------------------

