
# Calendar




1.  package com.msb.test02;
2.  import java.util.Calendar;
3.  import java.util.GregorianCalendar;
4.  /**
5.   * @Auther: msb-zhaoss
6.   */
7.  public class Test06 {
8.      //这是一个main方法，是程序的入口：
9.      public static void main(String[] args) {
10.         //Calendar是一个抽象类，不可以直接创建对象
11.         //GregorianCalendar()子类 extends Calendar（父类是一个抽象类）
12.         Calendar cal = new GregorianCalendar();
13.         Calendar cal2 = Calendar.getInstance();
14.         System.out.println(cal);
15.         //常用的方法：
16.         // get方法，传入参数：Calendar中定义的常量
17.         System.out.println(cal.get(Calendar.YEAR));
18.         System.out.println(cal.get(Calendar.MONTH));
19.         System.out.println(cal.get(Calendar.DATE));
20.         System.out.println(cal.get(Calendar.DAY_OF_WEEK));
21.        
    System.out.println(cal.getActualMaximum(Calendar.DATE));//获取当月日期的最大天数
22.        
    System.out.println(cal.getActualMinimum(Calendar.DATE));//获取当月日期的最小天数
23.         // set方法：可以改变Calendar中的内容
24.         cal.set(Calendar.YEAR,1990);
25.         cal.set(Calendar.MONTH,3);
26.         cal.set(Calendar.DATE,16);
27.         System.out.println(cal);
28.         //String--->Calendar:
29.         //分解：
30.         //String--->java.sql.Date:
31.         java.sql.Date date = java.sql.Date.valueOf("2020-4-5");
32.         //java.sql.Date-->Calendar:
33.         cal.setTime(date);
34.         System.out.println(cal);
35.     }
36. }

 






------------------------------------------------------------

