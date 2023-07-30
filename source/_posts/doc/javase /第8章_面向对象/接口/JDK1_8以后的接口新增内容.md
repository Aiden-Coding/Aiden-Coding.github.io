
# JDK1.8以后的接口新增内容

在JDK1.8之前，接口中只有两部分内容：
（1）常量：固定修饰符：public static final
（2）抽象方法：固定修饰符：public
abstract  




在JDK1.8之后，新增非抽象方法： 

（1）被public default修饰的非抽象方法： 

注意1：default修饰符必须要加上，否则出错 

注意2：实现类中要是想重写接口中的非抽象方法，那么default修饰符必须不能加，否则出错。 

1.  public interface TestInterface {
2.      //常量：
3.      public static final int NUM= 10;
4.      //抽象方法：
5.      public abstract void a();
6.      //public default修饰的非抽象方法：
7.      public default void b(){
8.          System.out.println("-------TestInterface---b()-----");
9.      }
10. }
11. class Test implements TestInterface{
12.     public void c(){
13.         //用一下接口中的b方法：
14.         b();//可以
15.         //super.b();不可以
16.         TestInterface.super.b();//可以
17.     }
18.     @Override
19.     public void a() {
20.         System.out.println("重写了a方法");
21.     }
22.     @Override
23.     public void b() {
24.     }
25. } 










（2）静态方法： 

注意1：static不可以省略不写 

注意2：静态方法不能重写 




1.  public interface TestInterface2 {
2.      //常量：
3.      public static final int NUM = 10;
4.      //抽象方法：
5.      public abstract  void a();
6.      //public default非抽象方法；
7.      public default void b(){
8.          System.out.println("-----TestInterface2---b");
9.      }
10.     //静态方法：
11.     public static void c(){
12.         System.out.println("TestInterface2中的静态方法");
13.     }
14. }
15. class Demo implements TestInterface2{
16.     @Override
17.     public void a() {
18.         System.out.println("重写了a方法");
19.     }
20.     public static void c(){
21.         System.out.println("Demo中的静态方法");
22.     }
23. }
24. class A {
25.     //这是一个main方法，是程序的入口：
26.     public static void main(String[] args) {
27.         Demo d = new Demo();
28.         d.c();
29.         Demo.c();
30.         TestInterface2.c();
31.     }
32. } 




疑问：为什么要在接口中加入非抽象方法？？？ 

如果接口中只能定义抽象方法的话，那么我要是修改接口中的内容，那么对实现类的影响太大了，所有实现类都会受到影响。 

现在在接口中加入非抽象方法，对实现类没有影响，想调用就去调用即可。 












------------------------------------------------------------

