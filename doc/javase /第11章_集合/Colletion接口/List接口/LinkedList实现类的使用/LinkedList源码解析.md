
# LinkedList源码解析

【1】JDK1.7和JDK1.8的LinkedList的源码是一致的 

【2】源码： 




1.  public class LinkedList<E>{//E是一个泛型，具体的类型要在实例化的时候才会最终确定
2.          transient int size = 0;//集合中元素的数量
3.          //Node的内部类
4.          private static class Node<E> {
5.          E item;//当前元素
6.          Node<E> next;//指向下一个元素地址
7.          Node<E> prev;//上一个元素地址
8.          Node(Node<E> prev, E element, Node<E> next) {
9.              this.item = element;
10.             this.next = next;
11.             this.prev = prev;
12.         }
13.     }
14.         transient Node<E> first;//链表的首节点
15.         transient Node<E> last;//链表的尾节点
16.         //空构造器：
17.         public LinkedList() {
18.     }
19.         //添加元素操作：
20.         public boolean add(E e) {
21.         linkLast(e);
22.         return true;
23.     }
24.         void linkLast(E e) {//添加的元素e
25.         final Node<E> l = last;//将链表中的last节点给l 如果是第一个元素的话 l为null
26.                 //将元素封装为一个Node具体的对象：
27.         final Node<E> newNode = new Node<>(l, e, null);
28.                 //将链表的last节点指向新的创建的对象：
29.         last = newNode;
30.                 
31.         if (l == null)//如果添加的是第一个节点
32.             first = newNode;//将链表的first节点指向为新节点
33.         else//如果添加的不是第一个节点 
34.             l.next = newNode;//将l的下一个指向为新的节点
35.         size++;//集合中元素数量加1操作
36.         modCount++;
37.     }
38.         //获取集合中元素数量
39.         public int size() {
40.         return size;
41.     }
42.         //通过索引得到元素：
43.         public E get(int index) {
44.         checkElementIndex(index);//健壮性考虑
45.         return node(index).item;
46.     }
47.         
48.     Node<E> node(int index) {
49.         //如果index在链表的前半段，那么从前往后找
50.         if (index < (size >> 1)) {
51.             Node<E> x = first;
52.             for (int i = 0; i < index; i++)
53.                 x = x.next;
54.             return x;
55.         } else {//如果index在链表的后半段，那么从后往前找
56.             Node<E> x = last;
57.             for (int i = size - 1; i > index; i--)
58.                 x = x.prev;
59.             return x;
60.         }
61.     }
62. } 






------------------------------------------------------------

