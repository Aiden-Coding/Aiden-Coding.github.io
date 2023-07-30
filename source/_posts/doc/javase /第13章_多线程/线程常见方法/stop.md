
# stop




1.  package com.msb.test09;
2.  /**
3.   * @author : msb-zhaoss
4.   */
5.  public class Demo {
6.      //这是main方法，程序的入口
7.      public static void main(String[] args) {
8.          for (int i = 1; i <= 100 ; i++) {
9.              if(i == 6){
10.                 Thread.currentThread().stop();//过期方法，不建议使用
11.             }
12.             System.out.println(i);
13.         }
14.     }
15. }

 






------------------------------------------------------------

