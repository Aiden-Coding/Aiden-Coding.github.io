﻿
# break

【1】通过练习感受break的作用：作用：停止循环： 

1.  public class TestFor02{
2.          public static void main(String[] args){
3.                  //功能：求1-100的和，当和第一次超过300的时候，停止程序
4.                  int sum = 0;
5.                  for(int i=1;i<=100;i++){	
6.                          sum += i;	
7.                          if(sum>300){//当和第一次超过300的时候
8.                                  //停止循环
9.                                  break;//停止循环
10.                         }
11.                         System.out.println(sum);
12.                 }
13.                 
14.         }
15. } 

【2】加深理解： 







1.  public class TestFor03{
2.          public static void main(String[] args){
3.                  //break的作用：停止最近的循环
4.                  /*
5.                  for(int i=1;i<=100;i++){
6.                          System.out.println(i);
7.                          if(i==36){
8.                                  break;//1-36
9.                          }
10.                 }
11.                 */
12.                 for(int i=1;i<=100;i++){
13.                         System.out.println(i);
14.                         while(i==36){
15.                                 break; //1-100 
    \---》break停止的是while循环，而不是外面的for循环
16.                         }
17.                 }
18.         }
19. } 

【3】break带标签的使用： 




1.  public class TestFor04{
2.          public static void main(String[] args){
3.                  outer:     ----》定义标签结束的位置
4.                  for(int i=1;i<=100;i++){
5.                          System.out.println(i);
6.                          while(i==36){
7.                                  break outer;    ----》根据标签来结束循环 
8.                          }
9.                  }
10.         }
11. } 

多层循环也可以使用标签，按照自己的需求去设定即可： 


![image](data:image/png;base64,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)

















------------------------------------------------------------

