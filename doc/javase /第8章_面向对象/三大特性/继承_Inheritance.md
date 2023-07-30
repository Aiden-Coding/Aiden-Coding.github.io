
# 继承(Inheritance)

【1】类是对对象的抽象： 

举例： 

荣耀20 ，小米 红米3，华为 p40 pro   ---> 类：手机类 




【2】继承是对类的抽象： 

举例： 

学生类：Student： 

属性：姓名，年龄，身高，学生编号 

方法：吃饭，睡觉，喊叫，学习 




教师类：Teacher: 

属性：姓名，年龄，身高，教师编号 

方法：吃饭，睡觉，喊叫，教学 




员工类：Emploee: 

属性：姓名，年龄，身高，员工编号 

方法：吃饭，睡觉，喊叫，工作 




共同的东西： 

人类： 

属性：姓名，年龄，身高 

方法：吃饭，睡觉，喊叫 




学生类/教师类/员工类  继承 自   人类   




以后定义代码： 

先定义人类： 

人类： ---》父类，基类，超类 

属性：姓名，年龄，身高 

方法：吃饭，睡觉，喊叫 




再定义 ： ---》子类，派生类 




学生类：Student： 

属性：学生编号 

方法：学习 




教师类：Teacher: 

属性：教师编号 

方法：教学 




员工类：Emploee: 

属性：员工编号 

方法：工作  







子类  继承自  父类  







狗类： 

属性：姓名，年龄，身高 

方法：吃饭，睡觉，喊叫 







我们的继承关系，是在合理的范围中进行的抽取 ，抽取出子类父类的关系： 

上面的案例中： 

学生类/教师类/员工类  继承 自   人类   ---》合理 

学生类/教师类/员工类  继承 自   狗类   ---》不合理 




区分： 

学生是一个人 

教师是一个人 

员工是一个人   ---》合理 




学生是一个狗    ---》不合理 




总结：继承 就是  is - a 的关系  







【3】代码层面的解释： 

先写父类，再写子类： 




父类：人类  Person 

子类：学生类   Student 







1.  package com.msb.test03;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Person {
6.      //属性：
7.      private int age;
8.      private String name;
9.      private double height;
10.     //提供setter getter方法：
11.     public int getAge() {
12.         return age;
13.     }
14.     public void setAge(int age) {
15.         this.age = age;
16.     }
17.     public String getName() {
18.         return name;
19.     }
20.     public void setName(String name) {
21.         this.name = name;
22.     }
23.     public double getHeight() {
24.         return height;
25.     }
26.     public void setHeight(double height) {
27.         this.height = height;
28.     }
29.     //方法：
30.     public void eat(){
31.         System.out.println("可以吃饭。。。");
32.     }
33.     public void sleep(){
34.         System.out.println("可以睡觉。。。");
35.     }
36. }

 




1.  package com.msb.test03;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Student extends Person {//子类Student 继承  父类Person
6.      //属性：
7.      private int sno;//学号
8.      public int getSno() {
9.          return sno;
10.     }
11.     public void setSno(int sno) {
12.         this.sno = sno;
13.     }
14.     //方法：
15.     public void study(){
16.         System.out.println("学生可以学习");
17.     }
18. }

 




1.  package com.msb.test03;
2.  /**
3.   * @Auther: msb-zhaoss
4.   */
5.  public class Test {
6.      //这是一个main方法，是程序的入口：
7.      public static void main(String[] args) {
8.          //创建子类Student的对象
9.          Student s = new Student();
10.         s.setSno(1001);
11.         s.setAge(18);
12.         s.setName("菲菲");
13.         s.setHeight(180.4);
14.         System.out.println("学生名字为："+s.getName()+",学生的年纪："+s.getAge());
15.         //访问方法：
16.         s.study();
17.         s.eat();
18.         s.sleep();
19.     }
20. }

 










【4】继承的好处：提高代码的复用性 

父类定义的内容，子类可以直接拿过来用就可以了，不用代码上反复重复定义了 




需要注意的点： 

父类private修饰的内容，子类实际上也继承，只是因为封装的特性阻碍了直接调用，但是提供了间接调用的方式，可以间接调用。 







【5】总结： 




（1）继承关系 ： 

父类/基类/超类 

子类/派生类 

子类继承父类一定在合理的范围进行继承的    子类 extends  父类 

（2）继承的好处： 

1.提高了代码的复用性，父类定义的内容，子类可以直接拿过来用就可以了，不用代码上反复重复定义了 

2.便于代码的扩展 

3.为了以后多态的使用。是多态的前提。 




（3）父类private修饰的内容，子类也继承过来了。 

（4）一个父类可以有多个子类。 

（5）一个子类只能有一个直接父类。 

但是可以间接的继承自其它类。 





![image](data:image/png;base64,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)



（6）继承具有传递性： 




Student --》继承自  Person  ---》继承自Object 

Object类是所有类的根基父类。 

所有的类都直接或者间接的继承自Object。 

























> 




------------------------------------------------------------

