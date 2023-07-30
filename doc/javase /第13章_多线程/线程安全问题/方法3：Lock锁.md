
# 方法3：Lock锁

【1】Lock锁引入： 

JDK1.5后新增新一代的线程同步方式:Lock锁 

与采用synchronized相比，lock可提供多种锁方案，更灵活 







synchronized是Java中的关键字，这个关键字的识别是靠JVM来识别完成的呀。是虚拟机级别的。 

但是Lock锁是API级别的，提供了相应的接口和对应的实现类，这个方式更灵活，表现出来的性能优于之前的方式。 







【2】代码演示： 







1.  package com.msb.test04;
2.  import java.util.concurrent.locks.Lock;
3.  import java.util.concurrent.locks.ReentrantLock;
4.  /**
5.   * @author : msb-zhaoss
6.   */
7.  public class BuyTicketThread implements Runnable {
8.      int ticketNum = 10;
9.      //拿来一把锁：
10.     Lock lock = new ReentrantLock();//多态  接口=实现类  可以使用不同的实现类
11.     @Override
12.     public void run() {
13.         //此处有1000行代码
14.         for (int i = 1; i <= 100 ; i++) {
15.             //打开锁：
16.             lock.lock();
17.             try{
18.                 if(ticketNum > 0){
19.                    
    System.out.println("我在"+Thread.currentThread().getName()+"买到了北京到哈尔滨的第" +
    ticketNum-- + "张车票");
20.                 }
21.             }catch (Exception ex){
22.                 ex.printStackTrace();
23.             }finally {
24.                 //关闭锁：--->即使有异常，这个锁也可以得到释放
25.                 lock.unlock();
26.             }
27.         }
28.         //此处有1000行代码
29.     }
30. }

 










【3】 Lock和synchronized的区别 




        1.Lock是显式锁（手动开启和关闭锁，别忘记关闭锁），synchronized是隐式锁 

        2.Lock只有代码块锁，synchronized有代码块锁和方法锁 

        3.使用Lock锁，JVM将花费较少的时间来调度线程，性能更好。并且具有更好的扩展性（提供更多的子类） 




【4】优先使用顺序： 




        Lock----同步代码块（已经进入了方法体，分配了相应资源）----同步方法（在方法体之外） 



------------------------------------------------------------

