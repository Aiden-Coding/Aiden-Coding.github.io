
# return

return的作用：跟循环无关，就是程序中遇到return那么return所在的那个方法就停止执行了： 




1.  public class TestFor08{
2.          public static void main(String[] args){
3.                  //return:遇到return结束当前正在执行的方法
4.                  for(int i=1;i<=100;i++){	
5.                          while(i==36){ 
6.                                  return;  
7.                          }
8.                          System.out.println(i);
9.                  }
10.                 
11.                 System.out.println("-----");
12.         }
13. } 






------------------------------------------------------------

