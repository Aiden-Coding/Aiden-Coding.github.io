
# TreeSet源码




1.  public class TreeSet<E> extends AbstractSet<E>
2.      implements NavigableSet<E>, Cloneable, java.io.Serializable{
3.                  //重要属性：
4.                  private transient NavigableMap<E,Object> m;
5.                  private static final Object PRESENT = new Object();
6.                  
7.                  //在调用空构造器的时候，底层创建了一个TreeMap
8.                  public TreeSet() {
9.                          this(new TreeMap<E,Object>());
10.                 }
11.                 
12.                 TreeSet(NavigableMap<E,Object> m) {
13.                         this.m = m;
14.                 }
15.                 
16.                 public boolean add(E e) {
17.         return m.put(e, PRESENT)==null;
18.     }
19.                 
20.                 
21.         } 






------------------------------------------------------------

