
# LinkedList实现类的使用




1.  package com.msb.test04;
2.  import java.util.Iterator;
3.  import java.util.LinkedList;
4.  /**
5.   * @author : msb-zhaoss
6.   */
7.  public class Test {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.         /*
11.         LinkedList常用方法：
12.         增加 addFirst(E e) addLast(E e)
13.              offer(E e) offerFirst(E e) offerLast(E e)
14.         删除 poll()
15.             pollFirst() pollLast()  ---》JDK1.6以后新出的方法，提高了代码的健壮性
16.             removeFirst() removeLast()
17.         修改
18.         查看 element()
19.              getFirst()  getLast()
20.              indexOf(Object o)   lastIndexOf(Object o)
21.              peek()
22.              peekFirst() peekLast()
23.         判断
24.          */
25.         //创建一个LinkedList集合对象：
26.         LinkedList<String> list = new LinkedList<>();
27.         list.add("aaaaa");
28.         list.add("bbbbb");
29.         list.add("ccccc");
30.         list.add("ddddd");
31.         list.add("eeeee");
32.         list.add("bbbbb");
33.         list.add("fffff");
34.         list.addFirst("jj");
35.         list.addLast("hh");
36.         list.offer("kk");//添加元素在尾端
37.         list.offerFirst("pp");
38.         list.offerLast("rr");
39.         System.out.println(list);//LinkedList可以添加重复数据
40.         System.out.println(list.poll());//删除头上的元素并且将元素输出
41.         System.out.println(list.pollFirst());
42.         System.out.println(list.pollLast());
43.         System.out.println(list.removeFirst());
44.         System.out.println(list.removeLast());
45.         System.out.println(list);//LinkedList可以添加重复数据
46.         /*list.clear();//清空集合
47.         System.out.println(list);*/
48.         /*System.out.println(list.pollFirst());*/
49.         /*System.out.println(list.removeFirst());报错：Exception in thread
    "main" java.util.NoSuchElementException*/
50.         //集合的遍历：
51.         System.out.println("---------------------");
52.         //普通for循环：
53.         for(int i = 0;i<list.size();i++){
54.             System.out.println(list.get(i));
55.         }
56.         System.out.println("---------------------");
57.         //增强for：
58.         for(String s:list){
59.             System.out.println(s);
60.         }
61.         System.out.println("---------------------");
62.         //迭代器：
63.         /*Iterator<String> it = list.iterator();
64.         while(it.hasNext()){
65.             System.out.println(it.next());
66.         }*/
67.         //下面这种方式好，节省内存
68.         for(Iterator<String> it = list.iterator();it.hasNext();){
69.             System.out.println(it.next());
70.         }
71.     }
72. }

 






------------------------------------------------------------

