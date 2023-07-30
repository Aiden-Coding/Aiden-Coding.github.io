
# 功能分解1：文件--》程序：FileReader

一个字符一个字符的将文件中的内容读取到程序中了： 




1.  package com.msb.io01;
2.  import java.io.File;
3.  import java.io.FileNotFoundException;
4.  import java.io.FileReader;
5.  import java.io.IOException;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.     //这是一个main方法，是程序的入口：
11.     public static void main(String[] args) throws IOException {
12.         //文件--》程序：
13.         //1.有一个文件：----》创建一个File类的对象
14.         File f = new File("d:\\Test.txt");
15.         //2.利用FileReader这个流，这个“管”怼到源文件上去   ---》创建一个FileReader的流的对象
16.         FileReader fr = new FileReader(f);
17.         //3.进行操作“吸”的动作  ---》读取动作
18.         /*下面的代码我们验证了：如果到了文件的结尾处，那么读取的内容为-1
19.         int n1 = fr.read();
20.         int n2 = fr.read();
21.         int n3 = fr.read();
22.         int n4 = fr.read();
23.         int n5 = fr.read();
24.         int n6 = fr.read();
25.         System.out.println(n1);
26.         System.out.println(n2);
27.         System.out.println(n3);
28.         System.out.println(n4);
29.         System.out.println(n5);
30.         System.out.println(n6);*/
31.         //方式1：
32.         /*int n = fr.read();
33.         while(n!=-1){
34.             System.out.println(n);
35.             n = fr.read();
36.         }*/
37.         //方式2：
38.         int n;
39.         while((n = fr.read())!=-1){
40.             System.out.println((char)n);
41.         }
42.         //4.“管”不用了，就要关闭  ---》关闭流
43.         //流，数据库，网络资源，靠jvm本身没有办法帮我们关闭，此时必须程序员手动关闭：
44.         fr.close();
45.     }
46. }

 




想一次性读取五个字符，不够的话下次再读五个字符： 




1.  package com.msb.io01;
2.  import java.io.File;
3.  import java.io.FileReader;
4.  import java.io.IOException;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test02 {
9.      //这是一个main方法，是程序的入口：
10.     public static void main(String[] args) throws IOException {
11.         //文件--》程序：
12.         //1.创建一个File类的对象
13.         File f = new File("d:\\Test.txt");
14.         //2.创建一个FileReader的流的对象
15.         FileReader fr = new FileReader(f);
16.         //3.读取动作
17.         //引入一个“快递员的小车”，这个“小车”一次拉5个快递：
18.         char[] ch = new char[5];//缓冲数组
19.         int len = fr.read(ch);//一次读取五个:返回值是这个数组中 的有效长度
20.         while(len!=-1){
21.             //System.out.println(len);
22.             //错误方式：
23.             /*for (int i = 0 ;i < ch.length;i++){
24.                 System.out.println(ch[i]);
25.             }*/
26.             //正确方式：
27.             /*for (int i = 0 ;i < len;i++){
28.                 System.out.println(ch[i]);
29.             }*/
30.             //正确方式2：将数组转为String：
31.             String str = new String(ch,0,len);
32.             System.out.print(str);
33.             len = fr.read(ch);
34.         }
35.         //4.关闭流
36.         fr.close();
37.     }
38. }

 















------------------------------------------------------------

