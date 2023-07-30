
# 利用try-catch-finally处理异常方式




1.  package com.msb.io01;
2.  import java.io.*;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test04 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args)  {
9.          //1.有一个源文件
10.         File f1 = new File("d:\\Test.txt");
11.         //2.有一个目标文件：
12.         File f2 = new File("d:\\Demo.txt");
13.         //3.搞一个输入的管 怼到源文件上：
14.         FileReader fr = null;
15.         FileWriter fw = null;
16.         try {
17.             fr = new FileReader(f1);
18.             //4.搞一个输出的管，怼到目标文件上：
19.             fw = new FileWriter(f2);
20.             //5.开始动作：
21.             char[] ch = new char[5];
22.             int len = fr.read(ch);
23.             while(len!=-1){
24.                 String s = new String(ch,0,len);
25.                 fw.write(s);
26.                 len = fr.read(ch);
27.             }
28.         } catch (FileNotFoundException e) {
29.             e.printStackTrace();
30.         } catch (IOException e) {
31.             e.printStackTrace();
32.         } finally {
33.             //6.关闭流：(关闭流的时候，倒着关闭，后用先关)
34.             try {
35.                 if(fw!=null){//防止空指针异常
36.                     fw.close();
37.                 }
38.             } catch (IOException e) {
39.                 e.printStackTrace();
40.             }
41.             try {
42.                 if(fr!=null){
43.                     fr.close();
44.                 }
45.             } catch (IOException e) {
46.                 e.printStackTrace();
47.             }
48.         }
49.     }
50. }

 






------------------------------------------------------------

