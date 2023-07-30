
# FileInputStream读取文件中内容

【1】读取文本文件： 




1.  package com.msb.io02;
2.  import java.io.File;
3.  import java.io.FileInputStream;
4.  import java.io.FileNotFoundException;
5.  import java.io.IOException;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.     //这是一个main方法，是程序的入口：
11.     public static void main(String[] args) throws IOException {
12.         //功能：利用字节流将文件中内容读到程序中来：
13.         //1.有一个源文件：
14.         File f = new File("D:\\Test.txt");
15.         //2.将一个字节流这个管 怼  到 源文件上：
16.         FileInputStream fis = new FileInputStream(f);
17.         //3.开始读取动作
18.         /*
19.         细节1：
20.         文件是utf-8进行存储的，所以英文字符 底层实际占用1个字节
21.         但是中文字符，底层实际占用3个字节。
22.         细节2：
23.         如果文件是文本文件，那么就不要使用字节流读取了，建议使用字符流。
24.         细节3：
25.         read()读取一个字节，但是你有没有发现返回值是 int类型，而不是byte类型？
26.         read方法底层做了处理，让返回的数据都是“正数”
27.         就是为了避免如果字节返回的是-1的话，那到底是读入的字节，还是到文件结尾呢。
28.          */
29.         int n = fis.read();
30.         while(n!=-1){
31.             System.out.println(n);
32.             n = fis.read();
33.         }
34.         //4.关闭流：
35.         fis.close();
36.     }
37. }

 




【2】利用字节流读取非文本文件：（以图片为案例：）--》一个字节一个字节的读取： 







1.  package com.msb.io02;
2.  import java.io.File;
3.  import java.io.FileInputStream;
4.  import java.io.IOException;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) throws IOException {
11.         //功能：利用字节流将文件中内容读到程序中来：
12.         //1.有一个源文件：
13.         File f = new File("D:\\LOL.jpg");
14.         //2.将一个字节流这个管 怼  到 源文件上：
15.         FileInputStream fis = new FileInputStream(f);
16.         //3.开始读取动作
17.         int count = 0;//定义一个计数器，用来计读入的字节的个数
18.         int n = fis.read();
19.         while(n!=-1){
20.             count++;
21.             System.out.println(n);
22.             n = fis.read();
23.         }
24.         System.out.println("count="+count);
25.         //4.关闭流：
26.         fis.close();
27.     }
28. }

 







【3】利用字节类型的缓冲数组： 




1.  package com.msb.io02;
2.  import java.io.File;
3.  import java.io.FileInputStream;
4.  import java.io.IOException;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) throws IOException {
11.         //功能：利用字节流将文件中内容读到程序中来：
12.         //1.有一个源文件：
13.         File f = new File("D:\\LOL.jpg");
14.         //2.将一个字节流这个管 怼  到 源文件上：
15.         FileInputStream fis = new FileInputStream(f);
16.         //3.开始读取动作
17.         //利用缓冲数组：（快递员的小车）
18.         byte[] b = new byte[1024*6];
19.         int len = fis.read(b);//len指的就是读取的数组中的有效长度
20.         while(len!=-1){
21.             //System.out.println(len);
22.             for(int i = 0;i<len;i++){
23.                 System.out.println(b[i]);
24.             }
25.             len = fis.read(b);
26.         }
27.         //4.关闭流：
28.         fis.close();
29.     }
30. }

 




































------------------------------------------------------------

