
# 双端队列Deque




1.  package com.msb.test08;
2.  import java.util.Collection;
3.  import java.util.Deque;
4.  import java.util.Iterator;
5.  import java.util.LinkedList;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test03 {
10.     //这是main方法，程序的入口
11.     public static void main(String[] args) {
12.         /*
13.         双端队列：
14.         Deque<E> extends Queue
15.         Queue一端放 一端取的基本方法  Deque是具备的
16.         在此基础上 又扩展了 一些 头尾操作（添加，删除，获取）的方法
17.          */
18.         Deque<String> d = new LinkedList<>() ;
19.         d.offer("A");
20.         d.offer("B");
21.         d.offer("C");
22.         System.out.println(d);//[A, B, C]
23.         d.offerFirst("D");
24.         d.offerLast("E");
25.         System.out.println(d);//[D, A, B, C, E]
26.         System.out.println(d.poll());
27.         System.out.println(d);//[A, B, C, E]
28.         System.out.println(d.pollFirst());
29.         System.out.println(d.pollLast());
30.         System.out.println(d);
31.                      System.out.println("认准一手微信：meetjava");
32.     }
33. }

 






------------------------------------------------------------

