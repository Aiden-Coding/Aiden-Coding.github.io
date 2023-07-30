
# LocalDate/LocalTime/LocalDateTime




1.  package com.msb.test02;
2.  import java.time.LocalDate;
3.  import java.time.LocalDateTime;
4.  import java.time.LocalTime;
5.  /**
6.   * @Auther: msb-zhaoss
7.   */
8.  public class Test09 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) {
11.         //1.完成实例化：
12.         //方法1：now()--获取当前的日期，时间，日期+时间
13.         LocalDate localDate = LocalDate.now();
14.         System.out.println(localDate);
15.         LocalTime localTime = LocalTime.now();
16.         System.out.println(localTime);
17.         LocalDateTime localDateTime = LocalDateTime.now();
18.         System.out.println(localDateTime);
19.         //方法2：of()--设置指定的日期，时间，日期+时间
20.         LocalDate of = LocalDate.of(2010, 5, 6);
21.         System.out.println(of);
22.         LocalTime of1 = LocalTime.of(12, 35, 56);
23.         System.out.println(of1);
24.         LocalDateTime of2 = LocalDateTime.of(1890, 12, 23, 13, 24, 15);
25.         System.out.println(of2);
26.         //LocalDate,LocalTime用的不如LocalDateTime多
27.         //下面讲解用LocalDateTime：
28.         //一些列常用的get***
29.         System.out.println(localDateTime.getYear());//2020
30.         System.out.println(localDateTime.getMonth());//JUNE
31.         System.out.println(localDateTime.getMonthValue());//6
32.         System.out.println(localDateTime.getDayOfMonth());//14
33.         System.out.println(localDateTime.getDayOfWeek());//SUNDAY
34.         System.out.println(localDateTime.getHour());//22
35.         System.out.println(localDateTime.getMinute());//22
36.         System.out.println(localDateTime.getSecond());//6
37.         //不是set方法，叫with
38.         //体会：不可变性
39.         LocalDateTime localDateTime2 = localDateTime.withMonth(8);
40.         System.out.println(localDateTime);
41.         System.out.println(localDateTime2);
42.         //提供了加减的操作：
43.         //加：
44.         LocalDateTime localDateTime1 = localDateTime.plusMonths(4);
45.         System.out.println(localDateTime);
46.         System.out.println(localDateTime1);
47.         //减：
48.         LocalDateTime localDateTime3 = localDateTime.minusMonths(5);
49.         System.out.println(localDateTime);
50.         System.out.println(localDateTime3);
51.     }
52. }

 






------------------------------------------------------------

