
# FileInputStream,FileOutputStream完成非文本文件的复制

【1】读入一个字节，写出一个字节： 




1.  package com.msb.io02;
2.  import java.io.*;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test04 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) throws IOException {
9.          //功能：完成图片的复制：
10.         //1.有一个源图片
11.         File f1 = new File("d:\\LOL.jpg");
12.         //2.有一个目标图片：
13.         File f2 = new File("d:\\LOL2.jpg");
14.         //3.有一个输入的管道 怼 到 源文件：
15.         FileInputStream fis = new FileInputStream(f1);
16.         //4.有一个输出的管道 怼到  目标文件上：
17.         FileOutputStream fos = new FileOutputStream(f2);
18.         //5.开始复制：（边读边写）
19.         int n = fis.read();
20.         while(n!=-1){
21.             fos.write(n);
22.             n = fis.read();
23.         }
24.         //6.关闭流：(倒着关闭流，先用后关)
25.         fos.close();
26.         fis.close();
27.     }
28. }

 

【2】利用缓冲字节数组： 




1.  package com.msb.io02;
2.  import java.io.File;
3.  import java.io.FileInputStream;
4.  import java.io.FileOutputStream;
5.  import java.io.IOException;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test05 {
10.     //这是一个main方法，是程序的入口：
11.     public static void main(String[] args) throws IOException {
12.         //功能：完成图片的复制：
13.         //1.有一个源图片
14.         File f1 = new File("d:\\LOL.jpg");
15.         //2.有一个目标图片：
16.         File f2 = new File("d:\\LOL2.jpg");
17.         //3.有一个输入的管道 怼 到 源文件：
18.         FileInputStream fis = new FileInputStream(f1);
19.         //4.有一个输出的管道 怼到  目标文件上：
20.         FileOutputStream fos = new FileOutputStream(f2);
21.         //5.开始复制：（边读边写）
22.         //利用缓冲数组：
23.         byte[] b = new byte[1024*8];
24.         int len = fis.read(b);
25.         while(len!=-1){
26.             fos.write(b,0,len);
27.             len = fis.read(b);
28.         }
29.         //6.关闭流：(倒着关闭流，先用后关)
30.         fos.close();
31.         fis.close();
32.     }
33. }

 












------------------------------------------------------------

