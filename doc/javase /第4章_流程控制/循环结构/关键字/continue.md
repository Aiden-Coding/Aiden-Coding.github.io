﻿
# continue

【1】通过案例感受continue的作用：结束本次循环，继续下一次循环 




1.  public class TestFor05{
2.          public static void main(String[] args){
3.                  //功能：输出1-100中被6整除的数：
4.                  //方式1：
5.                  /*
6.                  for(int i=1;i<=100;i++){	
7.                          if(i%6==0){//被6整除
8.                                  System.out.println(i);
9.                          }
10.                 }
11.                 */
12.                 
13.                 //方式2：
14.                 for(int i=1;i<=100;i++){	
15.                         if(i%6!=0){//不被6整除
16.                                 continue;//停止本次循环，继续下一次循环
17.                         }
18.                         System.out.println(i);
19.                 }
20.         }
21. } 

【2】加深理解： 




1.  public class TestFor06{
2.          public static void main(String[] args){
3.                  //continue:结束本次离它近的循环，继续下一次循环
4.                  /*
5.                  for(int i=1;i<=100;i++){	
6.                          if(i==36){
7.                                  continue;//1-100中间没有36
8.                          }
9.                          System.out.println(i);
10.                 }
11.                 */
12.                 
13.                 for(int i=1;i<=100;i++){	
14.                         while(i==36){
15.                                 System.out.println("------");
16.                                 continue; //1-35+死循环
17.                         }
18.                         System.out.println(i);
19.                 }
20.         }
21. } 

【3】continue带标签的使用： 

1.  public class TestFor07{
2.          public static void main(String[] args){
3.                  
4.                  outer:
5.                  for(int i=1;i<=100;i++){	
6.                          while(i==36){ 
7.                                  continue outer;  //1-100没有36
8.                          }
9.                          System.out.println(i);
10.                 }
11.         }
12. } 





![image](data:image/png;base64,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)











------------------------------------------------------------

