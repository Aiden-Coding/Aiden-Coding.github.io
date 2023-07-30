
# 源码（JDK1.7版本）




1.  public class HashMap<K,V>
2.      extends AbstractMap<K,V> //【1】继承的AbstractMap中，已经实现了Map接口
3.          //【2】又实现了这个接口，多余，但是设计者觉得没有必要删除，就这么地了
4.      implements Map<K,V>, Cloneable, Serializable{
5.                  
6.                  
7.          //【3】后续会用到的重要属性：先粘贴过来：
8.      static final int DEFAULT_INITIAL_CAPACITY = 16;//哈希表主数组的默认长度
9.          //定义了一个float类型的变量，以后作为：默认的装填因子，加载因子是表示Hsah表中元素的填满的程度
10.         //太大容易引起哈西冲突，太小容易浪费  0.75是经过大量运算后得到的最好值
11.         //这个值其实可以自己改，但是不建议改，因为这个0.75是大量运算得到的
12.         static final float DEFAULT_LOAD_FACTOR = 0.75f;
13.         transient Entry<K,V>[] table;//主数组,每个元素为Entry类型
14.         transient int size;
15.         int threshold;//数组扩容的界限值,门槛值   16*0.75=12 
16.         final float loadFactor;//用来接收装填因子的变量
17.         
18.         //【4】查看构造器：内部相当于：this(16,0.75f);调用了当前类中的带参构造器
19.         public HashMap() {
20.         this(DEFAULT_INITIAL_CAPACITY, DEFAULT_LOAD_FACTOR);
21.     }
22.         //【5】本类中带参数构造器：--》作用给一些数值进行初始化的！
23.         public HashMap(int initialCapacity, float loadFactor) {
24.         //【6】给capacity赋值，capacity的值一定是 大于你传进来的initialCapacity 的 最小的 2的倍数
25.         int capacity = 1;
26.         while (capacity < initialCapacity)
27.             capacity <<= 1;
28.                 //【7】给loadFactor赋值，将装填因子0.75赋值给loadFactor
29.         this.loadFactor = loadFactor;
30.                 //【8】数组扩容的界限值,门槛值
31.         threshold = (int)Math.min(capacity * loadFactor, MAXIMUM_CAPACITY +
    1);
32.                 
33.                 //【9】给table数组赋值，初始化数组长度为16
34.         table = new Entry[capacity];
35.                    
36.     }
37.         //【10】调用put方法：
38.         public V put(K key, V value) {
39.                 //【11】对空值的判断
40.         if (key == null)
41.             return putForNullKey(value);
42.                 //【12】调用hash方法，获取哈希码
43.         int hash = hash(key);
44.                 //【14】得到key对应在数组中的位置
45.         int i = indexFor(hash, table.length);
46.                 //【16】如果你放入的元素，在主数组那个位置上没有值，e==null  那么下面这个循环不走
47.                 //当在同一个位置上放入元素的时候
48.         for (Entry<K,V> e = table[i]; e != null; e = e.next) {
49.             Object k;
50.                         //哈希值一样  并且  equals相比一样   
51.                         //(k = e.key) == key  如果是一个对象就不用比较equals了
52.             if (e.hash == hash && ((k = e.key) == key || key.equals(k))) {
53.                 V oldValue = e.value;
54.                 e.value = value;
55.                 e.recordAccess(this);
56.                 return oldValue;
57.             }
58.         }
59.         modCount++;
60.                 //【17】走addEntry添加这个节点的方法：
61.         addEntry(hash, key, value, i);
62.         return null;
63.     }
64.         
65.         //【13】hash方法返回这个key对应的哈希值，内部进行二次散列，为了尽量保证不同的key得到不同的哈希码！
66.         final int hash(Object k) {
67.         int h = 0;
68.         if (useAltHashing) {
69.             if (k instanceof String) {
70.                 return sun.misc.Hashing.stringHash32((String) k);
71.             }
72.             h = hashSeed;
73.         }
74.                 //k.hashCode()函数调用的是key键值类型自带的哈希函数，
75.                 //由于不同的对象其hashCode()有可能相同，所以需对hashCode()再次哈希，以降低相同率。
76.         h ^= k.hashCode();
77.         // This function ensures that hashCodes that differ only by
78.         // constant multiples at each bit position have a bounded
79.         // number of collisions (approximately 8 at default load factor).
80.                 /*
81.                 接下来的一串与运算和异或运算，称之为“扰动函数”，
82.                 扰动的核心思想在于使计算出来的值在保留原有相关特性的基础上，
83.                 增加其值的不确定性，从而降低冲突的概率。
84.                 不同的版本实现的方式不一样，但其根本思想是一致的。
85.                 往右移动的目的，就是为了将h的高位利用起来，减少哈西冲突
86.                 */
87.         h ^= (h >>> 20) ^ (h >>> 12);
88.         return h ^ (h >>> 7) ^ (h >>> 4);
89.     }
90.         //【15】返回int类型数组的坐标
91.         static int indexFor(int h, int length) {
92.                 //其实这个算法就是取模运算：h%length，取模效率不如位运算
93.         return h & (length-1);
94.     }
95.         //【18】调用addEntry
96.         void addEntry(int hash, K key, V value, int bucketIndex) {
97.                 //【25】size的大小  大于
    16*0.75=12的时候，比如你放入的是第13个，这第13个你打算放在没有元素的位置上的时候
98.         if ((size >= threshold) && (null != table[bucketIndex])) {
99.                         //【26】主数组扩容为2倍
100.             resize(2 * table.length);
101.                         //【30】重新调整当前元素的hash码
102.             hash = (null != key) ? hash(key) : 0;
103.                         //【31】重新计算元素位置
104.             bucketIndex = indexFor(hash, table.length);
105.         }
106.                 //【19】将hash,key,value,bucketIndex位置  封装为一个Entry对象：
107.         createEntry(hash, key, value, bucketIndex);
108.     }
109.         //【20】
110.         void createEntry(int hash, K key, V value, int bucketIndex) {
111.                 //【21】获取bucketIndex位置上的元素给e
112.         Entry<K,V> e = table[bucketIndex];
113.                 //【22】然后将hash, key, value封装为一个对象，然后将下一个元素的指向为e （链表的头插法）
114.                 //【23】将新的Entry放在table[bucketIndex]的位置上
115.         table[bucketIndex] = new Entry<>(hash, key, value, e);
116.                 //【24】集合中加入一个元素 size+1
117.         size++;
118.     }
119.     //【27】
120.         void resize(int newCapacity) {
121.         Entry[] oldTable = table;
122.         int oldCapacity = oldTable.length;
123.         if (oldCapacity == MAXIMUM_CAPACITY) {
124.             threshold = Integer.MAX_VALUE;
125.             return;
126.         }
127.                 //【28】创建长度为newCapacity的数组
128.         Entry[] newTable = new Entry[newCapacity];
129.         boolean oldAltHashing = useAltHashing;
130.         useAltHashing |= sun.misc.VM.isBooted() &&
131.                 (newCapacity >= Holder.ALTERNATIVE_HASHING_THRESHOLD);
132.         boolean rehash = oldAltHashing ^ useAltHashing;
133.                 //【28.5】转让方法：将老数组中的东西都重新放入新数组中
134.         transfer(newTable, rehash);
135.                 //【29】老数组替换为新数组
136.         table = newTable;
137.                 //【29.5】重新计算
138.         threshold = (int)Math.min(newCapacity * loadFactor,
    MAXIMUM_CAPACITY + 1);
139.     }
140.         //【28.6】
141.         void transfer(Entry[] newTable, boolean rehash) {
142.         int newCapacity = newTable.length;
143.         for (Entry<K,V> e : table) {
144.             while(null != e) {
145.                 Entry<K,V> next = e.next;
146.                 if (rehash) {
147.                     e.hash = null == e.key ? 0 : hash(e.key);
148.                 }
149.                                 //【28.7】将哈希值，和新的数组容量传进去，重新计算key在新数组中的位置
150.                 int i = indexFor(e.hash, newCapacity);
151.                                 //【28.8】头插法
152.                 e.next = newTable[i];//获取链表上元素给e.next
153.                 newTable[i] = e;//然后将e放在i位置 
154.                 e = next;//e再指向下一个节点继续遍历
155.             }
156.         }
157.     }
158. } 






------------------------------------------------------------

