
# equals方法




1.  package com.msb.test02;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Phone {//手机类：
6.      //属性：
7.      private String brand;//品牌型号
8.      private double price;//价格
9.      private int year ;//出产年份
10.     //方法：
11.     public String getBrand() {
12.         return brand;
13.     }
14.     public void setBrand(String brand) {
15.         this.brand = brand;
16.     }
17.     public double getPrice() {
18.         return price;
19.     }
20.     public void setPrice(double price) {
21.         this.price = price;
22.     }
23.     public int getYear() {
24.         return year;
25.     }
26.     public void setYear(int year) {
27.         this.year = year;
28.     }
29.     @Override
30.     public String toString() {
31.         return "Phone{" +
32.                 "brand='" + brand + '\'' +
33.                 ", price=" + price +
34.                 ", year=" + year +
35.                 '}';
36.     }
37.     //构造器：
38.     public Phone() {
39.     }
40.     public Phone(String brand, double price, int year) {
41.         this.brand = brand;
42.         this.price = price;
43.         this.year = year;
44.     }
45.     //对equals方法进行重写：
46.     public boolean equals(Object obj) {//Object obj = new Phone();
47.         //将obj转为Phone类型：
48.         Phone other = (Phone)obj;//向下转型，为了获取子类中特有的内容
49.        
    if(this.getBrand()==other.getBrand()&&this.getPrice()==other.getPrice()&&thi
    .getYear()==other.getYear()){
50.             return true;
51.         }
52.         return false;
53.     }
54. }

 




1.  package com.msb.test02;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Test {
6.      //这是一个main方法，是程序的入口：
7.      public static void main(String[] args) {
8.          //创建Phone类的对象：
9.          Phone p1 = new Phone("华为P40",2035.98,2020);
10.         Phone p2 = new Phone("华为P40",2035.98,2020);
11.         //比较两个对象：p1和p2对象：
12.         //==的作用：比较左右两侧的值是否想的，要么相等，返回true,要么不相等,返回false
13.         System.out.println(p1==p2);//-->>>对于引用数据类型来说，比较的是地址值。--->一定返回的是false
14.         //Object类提供了一个方法 equals方法 ：作用：比较对象具体内容是否相等。
15.         boolean flag = p1.equals(p2);//点进源码发现：底层依旧比较的是==，比较的还是地址值。
16.         System.out.println(flag);
17.     }
18. }

 

总结： 

equals作用：这个方法提供了对对象的内容是否相等 的一个比较方式，对象的内容指的就是属性。 

父类Object提供的equals就是在比较==地址，没有实际的意义，我们一般不会直接使用父类提供的方法， 

而是在子类中对这个方法进行重写。 















------------------------------------------------------------

