
# Colletion接口常用方法



1.  package com.msb.test01;
2.  import java.util.ArrayList;
3.  import java.util.Arrays;
4.  import java.util.Collection;
5.  import java.util.List;
6.  /**
7.   * @author : msb-zhaoss
8.   */
9.  public class Test01 {
10.     //这是main方法，程序的入口
11.     public static void main(String[] args) {
12.         /*
13.         Collection接口的常用方法：
14.         增加：add(E e) addAll(Collection<? extends E> c)
15.         删除：clear() remove(Object o)
16.         修改：
17.         查看：iterator() size()
18.         判断：contains(Object o)  equals(Object o) isEmpty()
19.          */
20.         //创建对象：接口不能创建对象，利用实现类创建对象：
21.         Collection col = new ArrayList();
22.         //调用方法：
23.         //集合有一个特点：只能存放引用数据类型的数据，不能是基本数据类型
24.         //基本数据类型自动装箱，对应包装类。int--->Integer
25.         col.add(18);
26.         col.add(12);
27.         col.add(11);
28.         col.add(17);
29.         System.out.println(col/*.toString()*/);
30.         List list = Arrays.asList(new Integer[]{11, 15, 3, 7, 1});
31.         col.addAll(list);//将另一个集合添加入col中
32.         System.out.println(col);
33.         //col.clear();清空集合
34.         System.out.println(col);
35.         System.out.println("集合中元素的数量为："+col.size());
36.         System.out.println("集合是否为空："+col.isEmpty());
37.         boolean isRemove = col.remove(15);
38.         System.out.println(col);
39.         System.out.println("集合中数据是否被删除："+isRemove);
40.         Collection col2 = new ArrayList();
41.         col2.add(18);
42.         col2.add(12);
43.         col2.add(11);
44.         col2.add(17);
45.         Collection col3 = new ArrayList();
46.         col3.add(18);
47.         col3.add(12);
48.         col3.add(11);
49.         col3.add(17);
50.         System.out.println(col2.equals(col3));
51.         System.out.println(col2==col3);//地址一定不相等  false
52.         System.out.println("是否包含元素："+col3.contains(117));
53.     }
54. }

 






------------------------------------------------------------

