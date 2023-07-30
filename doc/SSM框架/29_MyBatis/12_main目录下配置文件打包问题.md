
# 12_main目录下配置文件打包问题




1.  <build>
2.      <!--告诉maven将项目源码中的xml文件也进行编译，并放到编译目录中-->
3.      <resources>
4.          <resource>
5.              <directory>src/main/java</directory>
6.              <includes>
7.                  <include>**/*.xml</include>
8.              </includes>
9.              <filtering>true</filtering>
10.         </resource>
11.         <resource>
12.             <directory>src/main/resources</directory>
13.             <filtering>true</filtering>
14.         </resource>
15.     </resources>
16. </build>

 






------------------------------------------------------------

