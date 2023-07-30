
# DateTimeFormatter




1.  package com.msb.test02;
2.  import java.time.LocalDateTime;
3.  import java.time.format.DateTimeFormatter;
4.  import java.time.format.FormatStyle;
5.  import java.time.temporal.TemporalAccessor;
6.  /**
7.   * @Auther: msb-zhaoss
8.   */
9.  public class Test10 {
10.     //这是一个main方法，是程序的入口：
11.     public static void main(String[] args) {
12.         //格式化类：DateTimeFormatter
13.         //方式一:预定义的标准格式。如: ISO_LOCAL_DATE_TIME;ISO_LOCAL_DATE;IS0_LOCAL_TIME
14.         DateTimeFormatter df1 = DateTimeFormatter.ISO_LOCAL_DATE_TIME;
15.         //df1就可以帮我们完成LocalDateTime和String之间的相互转换：
16.         //LocalDateTime-->String:
17.         LocalDateTime now = LocalDateTime.now();
18.         String str = df1.format(now);
19.         System.out.println(str);//2020-06-15T15:02:51.29
20.         //String--->LocalDateTime
21.         TemporalAccessor parse = df1.parse("2020-06-15T15:02:51.29");
22.         System.out.println(parse);
23.         //方式二:本地化相关的格式。如: oflocalizedDateTime()
24.         //参数：FormatStyle.LONG / FormatStyle.MEDIUM / FormatStyle.SHORT
25.         //FormatStyle.LONG :2020年6月15日 下午03时17分13秒
26.         //FormatStyle.MEDIUM: 2020-6-15 15:17:42
27.         //FormatStyle.SHORT:20-6-15 下午3:18
28.         DateTimeFormatter df2 =
    DateTimeFormatter.ofLocalizedDateTime(FormatStyle.SHORT);
29.         //LocalDateTime-->String:
30.         LocalDateTime now1 = LocalDateTime.now();
31.         String str2 = df2.format(now1);
32.         System.out.println(str2);
33.         //String--->LocalDateTime
34.         TemporalAccessor parse1 = df2.parse("20-6-15 下午3:18");
35.         System.out.println(parse1);
36.         //方式三: 自定义的格式。如: ofPattern( "yyyy-MM-dd hh:mm:ss") ---》重点，以后常用
37.         DateTimeFormatter df3 = DateTimeFormatter.ofPattern("yyyy-MM-dd
    hh:mm:ss");
38.         //LocalDateTime-->String:
39.         LocalDateTime now2 = LocalDateTime.now();
40.         String format = df3.format(now2);
41.         System.out.println(format);//2020-06-15 03:22:03
42.         //String--->LocalDateTime
43.         TemporalAccessor parse2 = df3.parse("2020-06-15 03:22:03");
44.         System.out.println(parse2);
45.     }
46. }

 






------------------------------------------------------------

