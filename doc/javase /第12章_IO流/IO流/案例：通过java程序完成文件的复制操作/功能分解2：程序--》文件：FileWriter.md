
# 功能分解2：程序--》文件：FileWriter

一个字符一个字符的向外输出： 







1.  package com.msb.io01;
2.  import java.io.File;
3.  import java.io.FileWriter;
4.  import java.io.IOException;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) throws IOException {
11.         //1.有个目标文件：
12.         File f = new File("d:\\demo.txt");
13.         //2.FileWriter管怼到文件上去：
14.         FileWriter fw = new FileWriter(f);
15.         //3.开始动作：输出动作：
16.         //一个字符一个字符的往外输出：
17.         String str = "hello你好";
18.         for (int i = 0 ;i < str.length();i++){
19.             fw.write(str.charAt(i));
20.         }
21.         //4.关闭流：
22.         fw.close();
23.     }
24. }

 

发现： 

如果目标文件不存在的话，那么会自动创建此文件。 

如果目标文件存在的话： 

[new FileWriter(f)](new FileWriter(f))   相当于对原文件进行覆盖操作。 

[new FileWriter(f,false)](new FileWriter(f,false))  相当于对源文件进行覆盖操作。不是追加。 

 [new FileWriter(f,true)](new FileWriter(f,true))   对原来的文件进行追加，而不是覆盖。 













利用缓冲数组：向外输出（利用缓冲数组：） 







1.  package com.msb.io01;
2.  import java.io.File;
3.  import java.io.FileWriter;
4.  import java.io.IOException;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) throws IOException {
11.         //1.有个目标文件：
12.         File f = new File("d:\\demo.txt");
13.         //2.FileWriter管怼到文件上去：
14.         FileWriter fw = new FileWriter(f,true);
15.         //3.开始动作：输出动作：
16.         //一个字符一个字符的往外输出：
17.         String str = "你好中国";
18.         char[] chars = str.toCharArray();
19.         fw.write(chars);
20.         //4.关闭流：
21.         fw.close();
22.     }
23. }

 















------------------------------------------------------------

