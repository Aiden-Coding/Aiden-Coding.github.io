
# 多态(Polymorphism)

【1】多态跟属性无关，多态指的是方法的多态，而不是属性的多态。 

【2】案例代入： 




1.  public class Animal {//父类：动物：
2.      public void shout(){
3.          System.out.println("我是小动物，我可以叫。。。");
4.      }
5.  } 




1.  public class Cat extends Animal{
2.      //喊叫方法：
3.      public void shout(){
4.          System.out.println("我是小猫，可以喵喵叫");
5.      }
6.      public void scratch(){
7.          System.out.println("我是小猫，我可以挠人");
8.      }
9.  } 




1.  public class Dog extends Animal{
2.      //喊叫：
3.      public void shout(){
4.          System.out.println("我是小狗，我可以汪汪叫");
5.      }
6.      public void guard(){
7.          System.out.println("我是小狗，我可以看家护院，保护我的小主人。。。");
8.      }
9.  } 




1.  public class Pig extends Animal{
2.      public void shout(){
3.          System.out.println("我是小猪，我嗯嗯嗯的叫");
4.      }
5.      public void eat(){
6.          System.out.println("我是小猪，我爱吃东西。。");
7.      }
8.  } 




1.  public class Girl {
2.      //跟猫玩耍：
3.      /*public void play(Cat cat){
4.          cat.shout();
5.      }*/
6.      //跟狗玩耍：
7.      /*public void play(Dog dog){
8.          dog.shout();
9.      }*/
10.     //跟小动物玩耍：
11.     public void play(Animal an){
12.         an.shout();
13.     }
14. } 




1.  public class Test {
2.      //这是一个main方法，是程序的入口：
3.      public static void main(String[] args) {
4.          //具体的猫：--》猫的对象
5.          //Cat c = new Cat();
6.          //具体的小女孩：--》女孩的对象
7.          Girl g = new Girl();
8.          //小女孩跟猫玩：
9.          //g.play(c);
10.         //具体的狗---》狗的对象：
11.         //Dog d = new Dog();
12.         //小女孩跟狗玩：
13.         //g.play(d);
14.         //具体的动物：--》动物的对象：
15.         //Cat c = new Cat();
16.         //Dog d = new Dog();
17.         Pig p = new Pig();
18.         Animal an = p;
19.         g.play(an);
20.     }
21. } 










【3】总结： 

（1）先有父类，再有子类：--》继承   先有子类，再抽取父类 ----》泛化  

（2）什么是多态： 

多态就是多种状态：同一个行为，不同的子类表现出来不同的形态。 

多态指的就是同一个方法调用，然后由于对象不同会产生不同的行为。 




（3）多态的好处： 

为了提高代码的扩展性，符合面向对象的设计原则：开闭原则。 

开闭原则：指的就是扩展是 开放的，修改是关闭的。 

注意：多态可以提高扩展性，但是扩展性没有达到最好，以后我们会学习 反射 




（4）多态的要素： 

一，继承：   Cat extends Animal  ,Pig extends Animal,   Dog extends Animal 

二，重写：子类对父类的方法shout()重写 

三， 父类引用指向子类对象： 




1.  Pig p = new Pig();
2.  Animal an = p; 

将上面的代码合为一句话： 

Animal an = new Pig(); 

=左侧：编译期的类型 

=右侧：运行期的类型 







Animal an = new Pig(); 

g.play(an); // 

1.  public void play(Animal an){//Animal an = an = new Pig();
2.          an.shout();
3.      } 




上面的代码，也是多态的一种非常常见的应用场合：父类当方法的形参，然后传入的是具体的子类的对象， 

然后调用同一个方法，根据传入的子类的不同展现出来的效果也不同，构成了多态。 
















































------------------------------------------------------------

