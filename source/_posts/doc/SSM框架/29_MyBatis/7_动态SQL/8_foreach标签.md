
# 8_foreach标签




1.  <!--List<Emp> findByEmpnos1(int[] empnos);
2.   collection=""  遍历的集合或者是数组
3.                   参数是数组,collection中名字指定为array
4.                   参数是List集合,collection中名字指定为list
5.   separator=""   多个元素取出的时候 用什么文字分隔
6.   open=""        以什么开头
7.   close=""       以什么结尾
8.   item=""        中间变量名
9.   for(Person per:PersonList)
10.  -->
11.  <select id="findByEmpnos1" resultType="emp">
12.      select * from emp  where empno in
13.      <foreach collection="array" separator="," open="(" close=")"
    item="deptno">
14.          #{deptno}
15.      </foreach>
16.  </select>
17. <!-- List<Emp> findByEmpnos2(List<Integer> empnos);-->
18.  <select id="findByEmpnos2" resultType="emp">
19.      select * from emp  where empno in
20.      <foreach collection="list" separator="," open="(" close=")"
    item="deptno">
21.          #{deptno}
22.      </foreach>
23.  </select>

 






------------------------------------------------------------

