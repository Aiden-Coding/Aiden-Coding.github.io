
# 转换流-InputStreamReader,OutputStreamWriter实现文本文件的复制




1.  package com.msb.io03;
2.  import java.io.*;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test02 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) throws IOException {
9.          //1.有一个源文件
10.         File f1 = new File("d:\\Test.txt");
11.         //2.有一个目标文件：
12.         File f2 = new File("d:\\Demo.txt");
13.         //3.输入方向：
14.         FileInputStream fis = new FileInputStream(f1);
15.         InputStreamReader isr = new InputStreamReader(fis,"utf-8");
16.         //4.输出方向：
17.         FileOutputStream fos = new FileOutputStream(f2);
18.         OutputStreamWriter osw = new OutputStreamWriter(fos,"gbk");
19.         //5.开始动作：
20.         char[] ch = new char[20];
21.         int len = isr.read(ch);
22.         while(len!=-1){
23.             osw.write(ch,0,len);
24.             len = isr.read(ch);
25.         }
26.         //6.关闭流：
27.         osw.close();
28.         isr.close();
29.     }
30. }

 






------------------------------------------------------------

