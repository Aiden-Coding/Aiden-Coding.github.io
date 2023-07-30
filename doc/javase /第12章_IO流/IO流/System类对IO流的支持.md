
# System类对IO流的支持

【1】System的属性： 

System.in  : “标准”输入流。---》默认情况下  从键盘输入 

System.out  :“标准”输出流。 ---》默认情况下，输出到控制台。 







【2】System.in ：“标准”输入流。---》默认情况下  从键盘输入 




1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws IOException {
4.          //得到的是标准的输入流：--》从键盘输入：
5.          //InputStream in = System.in;
6.          //调用方法：
7.          //int n = in.read();//read方法等待键盘的录入，所以这个方法是一个阻塞方法。
8.          //System.out.println(n);
9.          //以前案例：从键盘录入一个int类型的数据：
10.         //从上面的代码证明，键盘录入实际上是：System.in
11.         //形象的理解：System.in管，这个管怼到键盘上去了，所以你从键盘录入的话，就从这个管到程序中了
12.         //Scanner的作用：扫描器：起扫描作用的，扫键盘的从这根管出来的数据
13.         /*Scanner sc = new Scanner(System.in);
14.         int i = sc.nextInt();
15.         System.out.println(i);*/
16.         //既然Scanner是扫描的作用，不一定非得扫 System.in进来的东西，还可以扫描其他管的内容：
17.         Scanner sc = new Scanner(new FileInputStream(new
    File("d:\\Test.txt")));
18.         while(sc.hasNext()){
19.             System.out.println(sc.next());
20.         }
21.     }
22. } 










【3】System.out  : 返回的输出流 、 打印流（PrintStream） 




1.  package com.msb.io04;
2.  import java.io.PrintStream;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test02 {
7.      //这是一个main方法，是程序的入口：
8.      public static void main(String[] args) {
9.          //写到控制台：
10.         PrintStream out = System.out;
11.         //调用方法：
12.         out.print("你好1");//直接在控制台写出，但是不换行
13.         out.print("你好2");
14.         out.print("你好3");
15.         out.print("你好4");
16.         out.println("我是中国人1");//直接在控制台写出，并且换行操作
17.         out.println("我是中国人2");
18.         out.println("我是中国人3");
19.         out.println("我是中国人4");
20.         System.out.println("你是");
21.         System.out.print("中国人");
22.     }
23. }

 







































------------------------------------------------------------

