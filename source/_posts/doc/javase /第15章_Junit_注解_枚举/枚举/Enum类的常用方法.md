
# Enum类的常用方法




1.  package com.msb.enum03;
2.  /**
3.   * @author : msb-zhaoss
4.   */
5.  public class TestSeason {
6.      //这是一个main方法，是程序的入口：
7.      public static void main(String[] args) {
8.          //用enum关键字创建的Season枚举类上面的父类是：java.lang.Enum,常用方法子类Season可以直接拿过来使用：
9.          //toString();--->获取对象的名字
10.         Season autumn = Season.AUTUMN;
11.         System.out.println(autumn/*.toString()*/);//AUTUMN
12.         System.out.println("--------------------");
13.         //values:返回枚举类对象的数组
14.         Season[] values = Season.values();
15.         for(Season s:values){
16.             System.out.println(s/*.toString()*/);
17.         }
18.         System.out.println("--------------------");
19.         //valueOf：通过对象名字获取这个枚举对象
20.         //注意：对象的名字必须传正确，否则抛出异常
21.         Season autumn1 = Season.valueOf("AUTUMN");
22.         System.out.println(autumn1);
23.     }
24. }

 






------------------------------------------------------------

