
# java.util.Date




1.  package com.msb.test02;
2.  import java.util.Date;
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //java.util.Date:
10.         Date d = new Date();
11.         System.out.println(d);
12.         System.out.println(d.toString());
13.         System.out.println(d.toGMTString());//过期方法，过时方法，废弃方法。
14.         System.out.println(d.toLocaleString());
15.         System.out.println(d.getYear());//120+1900=2020
16.         System.out.println(d.getMonth());//5 :返回的值在 0 和 11 之间，值 0 表示 1 月。
17.         //返回自 1970 年 1 月 1 日 00:00:00 GMT 以来此 Date 对象表示的毫秒数。
18.         System.out.println(d.getTime());//1592055964263
19.         System.out.println(System.currentTimeMillis());
20.         /*
21.         （1）疑问：以后获取时间差用：getTime()还是currentTimeMillis()
22.         答案：currentTimeMillis()--》因为这个方法是静态的，可以类名.方法名直接调用
23.         （2）public static native long currentTimeMillis();
24.         本地方法
25.         为什么没有方法体？因为这个方法的具体实现不是通过java写的。
26.         （3）这个方法的作用：
27.         一般会去衡量一些算法所用的时间
28.          */
29.         long startTime = System.currentTimeMillis();
30.         for (int i = 0; i < 100000; i++) {
31.             System.out.println(i);
32.         }
33.         long endTime = System.currentTimeMillis();
34.         System.out.println(endTime-startTime);
35.     }
36. }

 






------------------------------------------------------------

