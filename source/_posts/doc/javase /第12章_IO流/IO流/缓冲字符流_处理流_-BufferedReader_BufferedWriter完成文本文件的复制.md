
# 缓冲字符流(处理流)-BufferedReader,BufferedWriter完成文本文件的复制




1.  package com.msb.io02;
2.  import java.io.*;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test07 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) throws IOException {
9.          //1.有一个源文件：
10.         File f1 = new File("d:\\Test.txt");
11.         //2.有一个目标文件：
12.         File f2 = new File("d:\\Demo.txt");
13.         //3.需要一个管 怼到 源文件：
14.         FileReader fr = new FileReader(f1);
15.         //4.需要一根管怼到目标文件：
16.         FileWriter fw = new FileWriter(f2);
17.         //5.套一根管在输入字符流外面：
18.         BufferedReader br = new BufferedReader(fr);
19.         //6.套一根管在输出字符流外面：
20.         BufferedWriter bw = new BufferedWriter(fw);
21.         //7.开始动作：
22.         //方式1：读取一个字符，输出一个字符：
23.         /*int n = br.read();
24.         while(n!=-1){
25.             bw.write(n);
26.             n = br.read();
27.         }*/
28.         //方式2:利用缓冲数组：
29.         /*char[] ch = new char[30];
30.         int len = br.read(ch);
31.         while(len!=-1){
32.             bw.write(ch,0,len);
33.             len = br.read(ch);
34.         }*/
35.         //方式3：读取String：
36.         String str = br.readLine();//每次读取文本文件中一行，返回字符串
37.         while(str!=null){
38.             bw.write(str);
39.             //在文本文件中应该再写出一个换行：
40.             bw.newLine();//新起一行
41.             str = br.readLine();
42.         }
43.         //8.关闭流
44.         bw.close();
45.         br.close();
46.     }
47. }

 






------------------------------------------------------------

