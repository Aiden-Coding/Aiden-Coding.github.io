
# Stack




1.  package com.msb.test01;
2.  import java.util.Stack;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          /*
10.         Stack是Vector的子类，Vector里面两个重要的属性：
11.         Object[] elementData;底层依然是一个数组
12.         int elementCount;数组中的容量
13.          */
14.         Stack s = new Stack();
15.         s.add("A");
16.         s.add("B");
17.         s.add("C");
18.         s.add("D");
19.         System.out.println(s);//[A, B, C, D]
20.         System.out.println("栈是否为空：" + s.empty());
21.         System.out.println("查看栈顶的数据，但是不移除：" + s.peek());
22.         System.out.println(s);
23.         System.out.println("查看栈顶的数据，并且不移除：" + s.pop());
24.         System.out.println(s);
25.         s.push("D");//和add方法执行的功能一样，就是返回值不同
26.         System.out.println(s);
27.     }
28. }

 






------------------------------------------------------------

