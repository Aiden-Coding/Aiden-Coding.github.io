
# catch中如何处理异常




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
16.         }catch(Exception ex){
17.             //第一种处理：什么都不写，什么都不做
18.             //第二种处理：输出自定义异常信息
19.             //System.out.println("对不起，你的代码有问题！");
20.             //第三种处理：打印异常信息：
21.             /*(1)调用toString方法，显示异常的类名（全限定路径）*/
22.             /*System.out.println(ex);
23.             System.out.println(ex.toString());*/
24.             /*(2)显示异常描述信息对应的字符串，如果没有就显示null
25.             System.out.println(ex.getMessage());*/
26.             /*(3)显示异常的堆栈信息：将异常信息捕获以后，在控制台将异常的效果给我们展示出来，方便我们查看异常*/
27.            /* ex.printStackTrace();*/
28.             //第四种处理：抛出异常：
29.             throw ex;
30.         }
31.         System.out.println("----谢谢你使用计算器111");
32.     }
33. }

 






------------------------------------------------------------

