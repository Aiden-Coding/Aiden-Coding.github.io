
# sleep

[https://go.zbj.com/news/20146.html](https://go.zbj.com/news/20146.html) （段子） 




【1】sleep : 人为的制造阻塞事件 




1.  public class Test01 {
2.      //这是main方法，程序的入口
3.      public static void main(String[] args) {
4.          try {
5.              Thread.sleep(3000);
6.          } catch (InterruptedException e) {
7.              e.printStackTrace();
8.          }
9.          System.out.println("00000000000000");
10.     }
11. }

 

【2】案例：完成秒表功能： 




1.  package com.msb.test08;
2.  import javafx.scene.input.DataFormat;
3.  import java.text.DateFormat;
4.  import java.text.SimpleDateFormat;
5.  import java.util.Date;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test02 {
10.     //这是main方法，程序的入口
11.     public static void main(String[] args) {
12.         //2.定义一个时间格式：
13.         DateFormat df = new SimpleDateFormat("HH:mm:ss");
14.         while(true){
15.             //1.获取当前时间：
16.             Date d = new Date();
17.             //3.按照上面定义的格式将Date类型转为指定格式的字符串：
18.             System.out.println(df.format(d));
19.             try {
20.                 Thread.sleep(1000);
21.             } catch (InterruptedException e) {
22.                 e.printStackTrace();
23.             }
24.         }
25.     }
26. }

 






------------------------------------------------------------

