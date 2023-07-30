
# HashSet底层原理




1.  public class HashSet<E>{
2.      //重要属性：
3.      private transient HashMap<E,Object> map;
4.      private static final Object PRESENT = new Object();
5.      //构造器：
6.      public HashSet() {
7.          map = new HashMap<>();//HashSet底层就是利用HashMap来完成的
8.      }
9.          
10.     public boolean add(E e) {
11.         return map.put(e, PRESENT)==null;
12.     }      
13. } 






------------------------------------------------------------

