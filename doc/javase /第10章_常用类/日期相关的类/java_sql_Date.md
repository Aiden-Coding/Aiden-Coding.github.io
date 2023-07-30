
# java.sql.Date




1.  package com.msb.test02;
2.  import java.sql.Date;
3.  /**
4.   * @Auther: msb-zhaoss
5.   */
6.  public class Test02 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //java.sql.Date:
10.         Date d = new Date(1592055964263L);
11.         System.out.println(d);
12.         /*
13.         (1)java.sql.Date和java.util.Date的区别：
14.         java.util.Date：年月日  时分秒
15.         java.sql.Date：年月日
16.         (2)java.sql.Date和java.util.Date的联系：
17.         java.sql.Date(子类) extends java.util.Date （父类）
18.          */
19.         //java.sql.Date和java.util.Date相互转换：
20.         //【1】util--->sql:
21.         java.util.Date date = new Date(1592055964263L);//创建util.Date的对象
22.         //方式1：向下转型
23.         Date date1 = (Date) date;
24.         /*
25.         父类：Animal 子类：Dog
26.         Animal an = new Dog();
27.         Dog d = (Dog)an;
28.          */
29.         //方式2：利用构造器
30.         Date date2 = new Date(date.getTime());
31.         //【2】sql-->util:
32.         java.util.Date date3 = d;
33.         //[3]String--->sql.Date:
34.         Date date4 =  Date.valueOf("2019-3-8");
35.     }
36. }

 






------------------------------------------------------------

