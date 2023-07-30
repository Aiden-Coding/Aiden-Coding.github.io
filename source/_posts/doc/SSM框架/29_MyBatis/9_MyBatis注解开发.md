
# 9_MyBatis注解开发




  




1.  public interface DeptMapper {
2.      Dept findDeptByDeptno(int deptno);
3.      @Select("select * from dept where deptno =#{deptno}")
4.      Dept findByDeptno(int deptno);
5.      @Update("update dept set dname =#{dname}, loc =#{loc} where deptno
    =#{deptno}")
6.      int updateDept(Dept dept);
7.      @Insert("insert into dept values(DEFAULT,#{dname},#{loc})")
8.      int addDept(Dept dept);
9.      @Delete("delete from dept where deptno =#{deptno}")
10.     int removeDept(int deptno);
11. }
12.   




1.使用注解没有实现Java代码和SQL语句的解耦 

2.无法实现SQL语句的动态拼接 

3.进行多表的查询时定制ResultMap比较麻烦 

  

**注解和XML的优缺点**             


|       |       |                                                                                                    |XML                                                                                                 |                                                                                                    |注解                                                                                                  |
|-------|----------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
|       |**优点**   |                                                                                                    |1.类和类之间的解耦                                                                                          |2.利于修改。直接修改XML文件，无需到源代码中修改。                                                                         |3.配置集中在XML中，对象间关系一目了然，利于快速了解项目和维护                                                                   |4.容易和其他系统进行数据交交换                                                                                    |                                                                                                    |1.简化配置                                                                                              |2.使用起来直观且容易，提升开发效率                                                                                  |3.类型安全，编译器进行校验，不用等到运行期才会发现错误。                                                                       |4.注解的解析可以不依赖于第三方库，可以直接使用Java自带的反射                                                                   |

  



------------------------------------------------------------

