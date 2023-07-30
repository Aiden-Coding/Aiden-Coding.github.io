
# TreeMap

【1】key的类型为String类型： 




1.  package com.msb.test11;
2.  import java.util.Map;
3.  import java.util.TreeMap;
4.  /**
5.   * @author : msb-zhaoss
6.   */
7.  public class Test02 {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.         Map<String,Integer> map = new TreeMap<>();
11.         map.put("blili",1234);
12.         map.put("alili",2345);
13.         map.put("blili",5467);
14.         map.put("clili",5678);
15.         map.put("dlili",2345);
16.         System.out.println(map.size());
17.         System.out.println(map);
18.     }
19. }

 

【2】key的类型是一个自定义的引用数据类型： 

（1）内部比较器： 




1.  package com.msb.test11;
2.  import java.util.Map;
3.  import java.util.TreeMap;
4.  /**
5.   * @author : msb-zhaoss
6.   */
7.  public class Test03 {
8.      //这是main方法，程序的入口
9.      public static void main(String[] args) {
10.         Map<Student,Integer> map = new TreeMap<>();
11.         map.put(new Student(19,"blili",170.5),1001);
12.         map.put(new Student(18,"blili",150.5),1003);
13.         map.put(new Student(19,"alili",180.5),1023);
14.         map.put(new Student(17,"clili",140.5),1671);
15.         map.put(new Student(10,"dlili",160.5),1891);
16.         System.out.println(map);
17.         System.out.println(map.size());
18.     }
19. }

 




1.  package com.msb.test11;
2.  /**
3.   * @author : msb-zhaoss
4.   */
5.  public class Student implements Comparable<Student>{
6.      private int age;
7.      private String name;
8.      private double height;
9.      public int getAge() {
10.         return age;
11.     }
12.     public void setAge(int age) {
13.         this.age = age;
14.     }
15.     public String getName() {
16.         return name;
17.     }
18.     public void setName(String name) {
19.         this.name = name;
20.     }
21.     public double getHeight() {
22.         return height;
23.     }
24.     public void setHeight(double height) {
25.         this.height = height;
26.     }
27.     public Student(int age, String name, double height) {
28.         this.age = age;
29.         this.name = name;
30.         this.height = height;
31.     }
32.     @Override
33.     public String toString() {
34.         return "Student{" +
35.                 "age=" + age +
36.                 ", name='" + name + '\'' +
37.                 ", height=" + height +
38.                 '}';
39.     }
40.     @Override
41.     public int compareTo(Student o) {
42.        /* return this.getAge()-o.getAge();*/
43.         return this.getName().compareTo(o.getName());
44.     }
45. }

 

（2）外部比较器： 




1.  package com.msb.test11;
2.  import java.util.Comparator;
3.  import java.util.Map;
4.  import java.util.TreeMap;
5.  /**
6.   * @author : msb-zhaoss
7.   */
8.  public class Test03 {
9.      //这是main方法，程序的入口
10.     public static void main(String[] args) {
11.         Map<Student,Integer> map = new TreeMap<>(new Comparator<Student>() {
12.             @Override
13.             public int compare(Student o1, Student o2) {
14.                 return
    ((Double)(o1.getHeight())).compareTo((Double)(o2.getHeight()));
15.             }
16.         });
17.         map.put(new Student(19,"blili",170.5),1001);
18.         map.put(new Student(18,"blili",150.5),1003);
19.         map.put(new Student(19,"alili",180.5),1023);
20.         map.put(new Student(17,"clili",140.5),1671);
21.         map.put(new Student(10,"dlili",160.5),1891);
22.         System.out.println(map);
23.         System.out.println(map.size());
24.     }
25. }

 






------------------------------------------------------------

