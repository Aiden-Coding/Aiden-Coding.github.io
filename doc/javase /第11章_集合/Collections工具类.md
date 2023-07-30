
# Collections工具类




1.  package com.msb.test12;
2.  import java.util.ArrayList;
3.  import java.util.Collections;
4.  /**
5.   * @author : msb-zhaoss
6.   */
7.  public class Test01 {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.         //Collections不支持创建对象，因为构造器私有化了
11.         /*Collections cols = new Collections();*/
12.         //里面的属性和方法都是被static修饰，我们可以直接用类名.去调用即可：
13.         //常用方法：
14.         //addAll：
15.         ArrayList<String> list = new ArrayList<>();
16.         list.add("cc");
17.         list.add("bb");
18.         list.add("aa");
19.         Collections.addAll(list,"ee","dd","ff");
20.         Collections.addAll(list,new String[]{"gg","oo","pp"});
21.         System.out.println(list);
22.         //binarySearch必须在有序的集合中查找：--》排序：
23.         Collections.sort(list);//sort提供的是升序排列
24.         System.out.println(list);
25.         //binarySearch
26.         System.out.println(Collections.binarySearch(list, "cc"));
27.         //copy:替换方法
28.         ArrayList<String> list2 = new ArrayList<>();
29.         Collections.addAll(list2,"tt","ss");
30.         Collections.copy(list,list2);//将list2的内容替换到list上去
31.         System.out.println(list);
32.         System.out.println(list2);
33.         //fill 填充
34.         Collections.fill(list2,"yyy");
35.         System.out.println(list2);
36.     }
37. }

 






------------------------------------------------------------

