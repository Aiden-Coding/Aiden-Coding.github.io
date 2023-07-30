
# InetAddress,InetSocketAddress

前情提要：File   ---》   封装盘符一个文件  

【1】InetAddress   ---》 封装了IP  




1.  public class Test01 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) throws UnknownHostException {
4.          //封装IP：
5.          //InetAddress ia = new
    InetAddress();不能直接创建对象，因为InetAddress()被default修饰了。
6.          InetAddress ia = InetAddress.getByName("192.168.199.217");
7.          System.out.println(ia);
8.          InetAddress ia2 =
    InetAddress.getByName("localhost");//localhost指代的是本机的ip地址
9.          System.out.println(ia2);
10.         InetAddress ia3 =
    InetAddress.getByName("127.0.0.1");//127.0.0.1指代的是本机的ip地址
11.         System.out.println(ia3);
12.         InetAddress ia4 = InetAddress.getByName("LAPTOP-CRIVSRRU");//封装计算机名
13.         System.out.println(ia4);
14.         InetAddress ia5 = InetAddress.getByName("www.mashibing.com");//封装域名
15.         System.out.println(ia5);
16.         System.out.println(ia5.getHostName());//获取域名
17.         System.out.println(ia5.getHostAddress());//获取ip地址
18.     }
19. }

 




【2】InetSocketAddress  ---》封装了IP，端口号 




1.  public class Test02 {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          InetSocketAddress isa = new
    InetSocketAddress("192.168.199.217",8080);
5.          System.out.println(isa);
6.          System.out.println(isa.getHostName());
7.          System.out.println(isa.getPort());
8.          InetAddress ia = isa.getAddress();
9.          System.out.println(ia.getHostName());
10.         System.out.println(ia.getHostAddress());
11.     }
12. } 


















------------------------------------------------------------

