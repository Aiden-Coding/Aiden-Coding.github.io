
# 10_Spring_CGLIB动态代理

提醒！！！  

如果大黄蜂播放器网校不是平凡之路、大飞机课堂，说明是翻录的，认准一手添加微信：meetjava 

如果大黄蜂播放器网校不是平凡之路、大飞机课堂，说明是翻录的，认准一手添加微信：meetjava 

如果大黄蜂播放器网校不是平凡之路、大飞机课堂，说明是翻录的，认准一手添加微信：meetjava 

另外，高价回收课程  

回收一切正版课程，买过任何正版课程的可以联系，支持换课，换VIP，或代下载，回收 

回收一切正版课程，买过任何正版课程的可以联系，支持换课，换VIP，或代下载，回收 

回收一切正版课程，买过任何正版课程的可以联系，支持换课，换VIP，或代下载，回收 

收藏下面学习目录链接，学课永不迷路，点击获取全网it目录  


[https://www.yuque.com/javadd/itcourse/list](https://www.yuque.com/javadd/itcourse/list)
 

微信：meetjava，认准一手，学习无忧，全网it课程都有 

微信：meetjava，认准一手，学习无忧，全网it课程都有 

重磅，收代理 冲冲冲  













proxy 动态代理 

面向接口 

1必须有接口和实现类   

2增强接口中定义的方法 

3只能读取接口中方法的上注解 




cglib动态代理模式 

面向父类 


![image](data:image/png;base64,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)






1.  package com.msb.testCglib;
2.  import org.junit.Test;
3.  import org.springframework.cglib.proxy.Enhancer;
4.  import org.springframework.cglib.proxy.MethodInterceptor;
5.  import org.springframework.cglib.proxy.MethodProxy;
6.  import java.lang.reflect.Method;
7.  /**
8.   * @Author: Ma HaiYang
9.   * @Description: MircoMessage:Mark_7001
10.  */
11. public class Test1 {
12.     @Test
13.     public void testCglib(){
14.         Person person =new Person();
15.         // 获取一个Person的代理对象
16.         // 1 获得一个Enhancer对象
17.         Enhancer enhancer=new Enhancer();
18.         // 2 设置父类字节码
19.         enhancer.setSuperclass(person.getClass());
20.         // 3 获取MethodIntercepter对象 用于定义增强规则
21.         MethodInterceptor methodInterceptor=new MethodInterceptor() {
22.             @Override
23.             public Object intercept(Object o, Method method, Object[]
    objects, MethodProxy methodProxy) throws Throwable {
24.                 /*Object o,  生成之后的代理对象 personProxy
25.                 Method method,  父类中原本要执行的方法  Person>>> eat()
26.                 Object[] objects, 方法在调用时传入的实参数组
27.                 MethodProxy methodProxy  子类中重写父类的方法 personProxy >>> eat()
28.                 */
29.                 Object res =null;
30.                 if(method.getName().equals("eat")){
31.                     // 如果是eat方法 则增强并运行
32.                     System.out.println("饭前洗手");
33.                     res=methodProxy.invokeSuper(o,objects);
34.                     System.out.println("饭后刷碗");
35.                 }else{
36.                     // 如果是其他方法 不增强运行
37.                     res=methodProxy.invokeSuper(o,objects); //
    子类对象方法在执行,默认会调用父类对应被重写的方法
38.                 }
39.                 return res;
40.             }
41.         };
42.         // 4 设置methodInterceptor
43.         enhancer.setCallback(methodInterceptor);
44.         // 5 获得代理对象
45.         Person personProxy = (Person)enhancer.create();
46.         // 6 使用代理对象完成功能
47.         personProxy.eat("包子");
48.     }
49. }
50. class Person  {
51.     public Person( ) {
52.     }
53.     public void eat(String foodName) {
54.         System.out.println("张三正在吃"+foodName);
55.     }
56. }

 
























------------------------------------------------------------
Generated with [Mybase Desktop 8.2.13](http://www.wjjsoft.com/mybase.html?ref=markdown_export)
