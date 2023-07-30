
# CopyOnWriteArraySet

【1】代码： 




1.  /**
2.   * @author : msb-zhaoss
3.   */
4.  public class Test02 {
5.      //这是main方法，程序的入口
6.      public static void main(String[] args) {
7.          //创建一个集合：
8.          CopyOnWriteArraySet<Integer> set = new CopyOnWriteArraySet<>();
9.          //在这里也体现出Set和List的本质区别，就在于是否重复
10.         //所以add方法直接不可以添加重复数据进去
11.         set.add(1);
12.         set.add(2);
13.         set.add(2);
14.         set.add(7);
15.         System.out.println(set);//[1, 2, 7]
16.         
17.     }
18. }

 

【2】源码： 




1.  public class CopyOnWriteArraySet<E>{
2.          //CopyOnWriteArraySet底层基于CopyOnWriteArrayList
3.          private final CopyOnWriteArrayList<E> al;
4.          
5.          public CopyOnWriteArraySet() {
6.          al = new CopyOnWriteArrayList<E>();
7.      }
8.          
9.          //添加方法：
10.         public boolean add(E e) {
11.         return al.addIfAbsent(e);//底层调用的还是CopyOnWriteArrayList的addIfAbsent
12.     }
13. } 

总结： 




由上面的源码看出，每次调用[CopyOnWriteArraySet](CopyOnWriteArraySet)的add方法时候，其实底层是基于CopyOnWriteArrayList的addIfAbsent， 

每次在addIfAbsent方法中每次都要对数组进行遍历，所以CopyOnWriteArraySet的性能低于CopyOnWriteArrayList 












------------------------------------------------------------

