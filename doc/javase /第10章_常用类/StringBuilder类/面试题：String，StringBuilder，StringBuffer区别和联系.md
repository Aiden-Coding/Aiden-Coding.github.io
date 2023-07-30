
# 面试题：String，StringBuilder，StringBuffer区别和联系

### String、StringBuffer、StringBuilder区别与联系 

1. String类是不可变类，即一旦一个String对象被创建后，包含在这个对象中的字符序列是不可改变的，直至这个对象销毁。 

2.
StringBuffer类则代表一个字符序列可变的字符串，可以通过append、insert、reverse、setChartAt、setLength等方法改变
内容。一旦生成了最终的字符串，调用toString方法将其转变为String 

3.
JDK1.5新增了一个StringBuilder类，与StringBuffer相似，构造方法和方法基本相同。不同是StringBuffer是线程安全的，而Str
ngBuilder是线程不安全的，所以性能略高。通常情况下，创建一个内容可变的字符串，应该优先考虑使用StringBuilder 

StringBuilder:JDK1.5开始  效率高   线程不安全 

StringBuffer:JDK1.0开始   效率低    线程安全 



------------------------------------------------------------

