
# List接口的常用方法和遍历方式



1.  package com.msb.test01;
2.  import com.sun.org.apache.xerces.internal.dom.PSVIAttrNSImpl;
3.  import java.util.ArrayList;
4.  import java.util.Iterator;
5.  import java.util.List;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test03 {
10.     //这是main方法，程序的入口
11.     public static void main(String[] args) {
12.         /*
13.         List接口中常用方法：
14.         增加：add(int index, E element)
15.         删除：remove(int index)  remove(Object o)
16.         修改：set(int index, E element)
17.         查看：get(int index)
18.         判断：
19.          */
20.         List list = new ArrayList();
21.         list.add(13);
22.         list.add(17);
23.         list.add(6);
24.         list.add(-1);
25.         list.add(2);
26.         list.add("abc");
27.         System.out.println(list);
28.         list.add(3,66);
29.         System.out.println(list);
30.         list.set(3,77);
31.         System.out.println(list);
32.         list.remove(2);//在集合中存入的是Integer类型数据的时候，调用remove方法调用的是：remove(int
    index)
33.         System.out.println(list);
34.         list.remove("abc");
35.         System.out.println(list);
36.         Object o = list.get(0);
37.         System.out.println(o);
38.         //List集合 遍历：
39.         //方式1：普通for循环：
40.         System.out.println("---------------------");
41.         for(int i = 0;i<list.size();i++){
42.             System.out.println(list.get(i));
43.         }
44.         //方式2：增强for循环：
45.         System.out.println("---------------------");
46.         for(Object obj:list){
47.             System.out.println(obj);
48.         }
49.         //方式3：迭代器：
50.         System.out.println("---------------------");
51.         Iterator it = list.iterator();
52.         while(it.hasNext()){
53.             System.out.println(it.next());
54.         }
55.     }
56. }

 






------------------------------------------------------------

