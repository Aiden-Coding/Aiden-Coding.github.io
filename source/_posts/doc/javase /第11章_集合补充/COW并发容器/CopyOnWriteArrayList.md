
# CopyOnWriteArrayList






【1】代码： 




1.  package com.msb.test04;
2.  import java.util.concurrent.CopyOnWriteArrayList;
3.  /**
4.   * @author : msb-zhaoss
5.   */
6.  public class Test {
7.      //这是main方法，程序的入口
8.      public static void main(String[] args) {
9.          CopyOnWriteArrayList<Integer> list = new CopyOnWriteArrayList<>();
10.         //添加方法：
11.         list.add(1);
12.         list.add(2);
13.         list.add(3);
14.         list.add(4);
15.         System.out.println(list);//[1, 2, 3, 4]
16.         list.add(3);//add方法无论元素是否存在，都可以添加进去--》添加重复的元素
17.         System.out.println(list);//[1, 2, 3, 4, 3]
18.         //adj. 缺席的；缺少的；心不在焉的；茫然的
19.         list.addIfAbsent(33);//添加不存在的元素--》不可以添加重复的数据
20.         System.out.println(list);//[1, 2, 3, 4, 3, 33]
21.     }
22. }

 

【2】源码分析： 







1.  public class CopyOnWriteArrayList<E>{
2.          //底层基于数组实现的
3.          private transient volatile Object[] array;
4.          
5.          public CopyOnWriteArrayList() {
6.          setArray(new Object[0]);
7.      }
8.          
9.          final void setArray(Object[] a) {
10.         array = a; // array = new Object[0]
11.     }
12.         //add方法：
13.         public boolean add(E e) {
14.         final ReentrantLock lock = this.lock;
15.         lock.lock();
16.         try {
17.                         //返回底层array数组,给了elements
18.             Object[] elements = getArray();
19.                         //获取elements的长度---》获取老数组的长度
20.             int len = elements.length;
21.                         //完成数组的复制，将老数组中的元素复制到新数组中，并且新数组的长度加1操作
22.             Object[] newElements = Arrays.copyOf(elements, len + 1);
23.                         //将e元素放入新数组最后位置
24.             newElements[len] = e;
25.                         //array数组的指向从老数组变为新数组
26.             setArray(newElements);
27.             return true;
28.         } finally {
29.             lock.unlock();
30.         }
31.     }
32.         
33.         
34.         final Object[] getArray() {
35.         return array;//返回底层数组
36.     }
37.         
38.         
39.         private boolean addIfAbsent(E e, Object[] snapshot) {
40.         final ReentrantLock lock = this.lock;
41.         lock.lock();
42.         try {
43.                         //取出array数组给current
44.             Object[] current = getArray();
45.             int len = current.length;
46.             if (snapshot != current) {
47.                 // Optimize for lost race to another addXXX operation
48.                 int common = Math.min(snapshot.length, len);
49.                                 //遍历老数组：
50.                 for (int i = 0; i < common; i++)
51.                                         //eq(e,
    current[i])将放入的元素和老数组的每一个元素进行比较，如果有重复的元素，就返回false，不添加了
52.                     if (current[i] != snapshot[i] && eq(e, current[i]))
53.                         return false;
54.                 if (indexOf(e, current, common, len) >= 0)
55.                         return false;
56.             }
57.                         //完成数组的复制，将老数组中的元素复制到新数组中，并且新数组的长度加1操作
58.             Object[] newElements = Arrays.copyOf(current, len + 1);
59.                         //将e元素放入新数组最后位置
60.             newElements[len] = e;
61.                         //array数组的指向从老数组变为新数组
62.             setArray(newElements);
63.             return true;
64.         } finally {
65.             lock.unlock();
66.         }
67.     }
68.         
69.         
70. } 


















------------------------------------------------------------

