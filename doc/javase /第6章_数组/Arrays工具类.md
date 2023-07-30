
# Arrays工具类

为了方便我们对数组进行操作，系统提供一个类Arrays，我们将它当做工具类来使用。 




1.  import java.util.Arrays;
2.  public class TestArray13{
3.          public static void main(String[] args){
4.                  //给定一个数组：
5.                  int[] arr = {1,3,7,2,4,8};
6.                  //toString:对数组进行遍历查看的，返回的是一个字符串，这个字符串比较好看
7.                  System.out.println(Arrays.toString(arr));
8.                  
9.                  //binarySearch:二分法查找：找出指定数组中的指定元素对应的索引：
10.                 //这个方法的使用前提：一定要查看的是一个有序的数组：
11.                 //sort：排序 -->升序
12.                 Arrays.sort(arr);
13.                 System.out.println(Arrays.toString(arr));
14.                 System.out.println(Arrays.binarySearch(arr,4));
15.                 
16.                 int[] arr2 = {1,3,7,2,4,8};
17.                 //copyOf:完成数组的复制：
18.                 int[] newArr = Arrays.copyOf(arr2,4);
19.                 System.out.println(Arrays.toString(newArr));
20.                 
21.                 //copyOfRange:区间复制：
22.                 int[] newArr2 =
    Arrays.copyOfRange(arr2,1,4);//[1,4)-->1,2,3位置
23.                 System.out.println(Arrays.toString(newArr2));
24.                 
25.                 //equals:比较两个数组的值是否一样：
26.                 int[] arr3 = {1,3,7,2,4,8};
27.                 int[] arr4 = {1,3,7,2,4,8};
28.                 System.out.println(Arrays.equals(arr3,arr4));//true
29.                 System.out.println(arr3==arr4);//false
    ==比较左右两侧的值是否相等，比较的是左右的地址值，返回结果一定是false
30.                 
31.                 //fill：数组的填充：
32.                 int[] arr5 = {1,3,7,2,4,8};
33.                 Arrays.fill(arr5,10);
34.                 System.out.println(Arrays.toString(arr5));
35.         }
36. } 






------------------------------------------------------------

