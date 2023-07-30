
# join

join方法：当一个线程调用了join方法，这个线程就会先被执行，它执行结束以后才可以去执行其余的线程。 

注意：必须先start，再join才有效。 







1.  package com.msb.test07;
2.  /**
3.   * @author : msb-zhaoss
4.   */
5.  public class TestThread extends Thread {
6.      public TestThread(String name){
7.          super(name);
8.      }
9.      @Override
10.     public void run() {
11.         for (int i = 1; i <= 10 ; i++) {
12.             System.out.println(this.getName()+"----"+i);
13.         }
14.     }
15. }
16. class Test{
17.     //这是main方法，程序的入口
18.     public static void main(String[] args) throws InterruptedException {
19.         for (int i = 1; i <= 100 ; i++) {
20.             System.out.println("main-----"+i);
21.             if(i == 6){
22.                 //创建子线程：
23.                 TestThread tt = new TestThread("子线程");
24.                 tt.start();
25.                 tt.join();//“半路杀出个程咬金”
26.             }
27.         }
28.     }
29. }

 






------------------------------------------------------------

