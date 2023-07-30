
# 功能分解3：利用FileReader，FileWriter文件复制




1.  package com.msb.io01;
2.  import java.io.*;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test04 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) throws IOException {
9.          //1.有一个源文件
10.         File f1 = new File("d:\\Test.txt");
11.         //2.有一个目标文件：
12.         File f2 = new File("d:\\Demo.txt");
13.         //3.搞一个输入的管 怼到源文件上：
14.         FileReader fr = new FileReader(f1);
15.         //4.搞一个输出的管，怼到目标文件上：
16.         FileWriter fw = new FileWriter(f2);
17.         //5.开始动作：
18.         //方式1：一个字符一个字符的复制：
19.         /*int n = fr.read();
20.         while(n!=-1){
21.             fw.write(n);
22.             n = fr.read();
23.         }*/
24.         //方式2：利用缓冲字符数组：
25.         /*char[] ch = new char[5];
26.         int len = fr.read(ch);
27.         while(len!=-1){
28.             fw.write(ch,0,len);//将缓冲数组中有效长度写出
29.             len = fr.read(ch);
30.         }*/
31.         //方式3：利用缓冲字符数组，将数组转为String写出。
32.         char[] ch = new char[5];
33.         int len = fr.read(ch);
34.         while(len!=-1){
35.             String s = new String(ch,0,len);
36.             fw.write(s);
37.             len = fr.read(ch);
38.         }
39.         //6.关闭流：(关闭流的时候，倒着关闭，后用先关)
40.         fw.close();
41.         fr.close();
42.     }
43. }

 






------------------------------------------------------------

