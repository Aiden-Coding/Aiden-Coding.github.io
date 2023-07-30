
# 可以作为Class类的实例的种类

Class类的具体的实例： 

（1）类：外部类，内部类 

（2）接口 

（3）注解 

（4）数组 

（5）基本数据类型 

（6）void 




验证： 




1.  package com.zhaoss.test02;
2.  public class Demo {
3.      public static void main(String[] args) {
4.          /*
5.          Class类的具体的实例：
6.          （1）类：外部类，内部类
7.          （2）接口
8.          （3）注解
9.          （4）数组
10.         （5）基本数据类型
11.         （6）void
12.          */
13.         Class c1 = Person.class;
14.         Class c2 = Comparable.class;
15.         Class c3 = Override.class;
16.         int[] arr1 = {1,2,3};
17.         Class c4 = arr1.getClass();
18.         int[] arr2 = {5,6,7};
19.         Class c5 = arr2.getClass();
20.         System.out.println(c4==c5);//结果：true .同一个维度，同一个元素类型,得到的字节码就是同一个
21.         
22.         Class c6 = int.class;
23.         Class c7 = void.class;
24.     }
25. }

 






------------------------------------------------------------

