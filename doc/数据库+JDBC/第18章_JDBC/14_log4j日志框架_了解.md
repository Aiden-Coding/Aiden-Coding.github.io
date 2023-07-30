
# 14_log4j日志框架_了解

###  log4j日志处理 

**1)**     **什么是日志log** 

异常信息  登录成功失败的信息  其他重要操作的信息 

日志可以记录程序的运行状态,运行信息,用户的一些常用操作.日志可以帮助我们分析程序的运行状态,帮我们分析用户的操作习惯,进而对程序进行改进 

**2)**     **如何记录日志** 

方式1：System.out.println(.....)    e.printStackTrace(); 

缺点：不是保存到文件，不能长久存储 

方式2：IO流 将System.out.println(.....)  e.printStackTrace();写入文件 

缺点：操作繁琐,IO流操作容易阻塞线程,日志没有等级,日志的格式不能很好的定制,要想实行编程复杂 

方式3：使用现成的日志框架，比如log4j 

优点：1长久保存 2有等级3格式可以很好的定制 4代码编写简单 

**3)**     **log4j日志的级别** 

    FATAL：  指出现非常严重的错误事件，这些错误可能导致应用程序异常中止 

    ERROR： 指虽有错误，但仍允许应用程序继续运行 

WARN：  指运行环境潜藏着危害 

    INFO：    指报告信息，这些信息在粗粒度级别上突出显示应用程序的进程 

    DEBUG： 指细粒度信息事件，对于应用程序的调试是最有用的 

**4)**     **使用log4j记录日志** 

    1.加入jar包   log4j-1.2.8.jar 

2.加入属性文件 src 下 log4j.properties 




1.  log4j.rootLogger=error,logfile
2.  log4j.appender.stdout=org.apache.log4j.ConsoleAppender
3.  log4j.appender.stdout.Target=System.err
4.  log4j.appender.stdout.layout=org.apache.log4j.SimpleLayout
5.  log4j.appender.logfile=org.apache.log4j.FileAppender
6.  log4j.appender.logfile.File=d:/msb.log
7.  log4j.appender.logfile.layout=org.apache.log4j.PatternLayout
8.  log4j.appender.logfile.layout.ConversionPattern=%d{yyyy-MM-dd   HH:mm:ss}
    %l %F %p %m%n 




    通过属性文件理解log4j的主要API 

Appender 日志目的地 :ConsoleAppender  FileAppender 

Layout 日志格式化器 ：SimpleLayout  PatternLayout 

3.代码中记录日志   


|                                                                                                                                                                                                                    |//创建一个日志记录器
  private static final Logger logger =   Logger.getLogger(DBUtil.class.getName());                                                                                                                      |                                                                                                                                                                                                                    |//在合适的地方添加日志                                                                                                                                                                                                        |logger.info("正确的读取了属性文件："+prop);                                                                                                                                                                                    |logger.debug("正确的关闭了结果集");                                                                                                                                                                                          |logger.error("DML操作错误："+e);                                                                                                                                                                                         |

  

**5)**     **理解日志格式化字符的含义 **

%p：输出日志信息的优先级，即DEBUG，INFO，WARN，ERROR，FATAL。 

%d：输出日志时间点的日期或时间，默认格式为ISO8601，也可以在其后指定格式，如：%d{yyyy/MM/dd HH:mm:ss,SSS}。 

%r：输出自应用程序启动到输出该log信息耗费的毫秒数。 

%t：输出产生该日志事件的线程名。 

%l：输出日志事件的发生位置，相当于%c.%M(%F:%L)的组合，包括类全名、方法、文件名以及在代码中的行数。例如 

test.TestLog4j.main(TestLog4j.java:10)。
       %c：输出日志信息所属的类目，通常就是所在类的全名。
     
 %M：输出产生日志信息的方法名。
       %F：输出日志消息产生时所在的文件名称。
       %L:：输出代码中的行号。
       %m:：输出代码中指定的具体日志信息。
%n：输出一个回车换行符，Windows平台为"rn"，Unix平台为"n"。
       %x：输出和当前线程相关联的NDC(嵌套诊断环境)，尤其用到像java servlets
这样的多客户多线程的应用中。
       %%：输出一个"%"字符。 

**6)**     **使用log4j记录日志 连接池中通过log4j记录日志** 

**
**

1.  **package com.msb.dao;**
2.  **import com.msb.util.PropertiesUtil;**
3.  **import org.apache.log4j.Logger;**
4.  **import java.sql.Connection;**
5.  **import java.sql.DriverManager;**
6.  **import java.sql.SQLException;**
7.  **import java.util.LinkedList;**
8.  **/****
9.  ** * @Author: Ma HaiYang**
10. ** * @Description: MircoMessage:Mark_7001**
11. ** */**
12. **public class MyConnectionPool {**
13. **    private static String driver;**
14. **    private static String url;**
15. **    private static String user;**
16. **    private static String password;**
17. **    private static int initSize;**
18. **    private static int maxSize;**
19. **    private static Logger logger;**
20. **    private static LinkedList<Connection> pool;**
21. **    static{**
22. **        logger=Logger.getLogger(MyConnectionPool.class);**
23. **        // 初始化参数**
24. **        PropertiesUtil propertiesUtil=new
    PropertiesUtil("/jdbc.properties");**
25. **        driver=propertiesUtil.getProperties("driver");**
26. **        url=propertiesUtil.getProperties("url");**
27. **        user=propertiesUtil.getProperties("user");**
28. **        password=propertiesUtil.getProperties("password");**
29. **        initSize=Integer.parseInt(propertiesUtil.getProperties("initSize"));**
30. **        maxSize=Integer.parseInt(propertiesUtil.getProperties("maxSize"));**
31. **        // 加载驱动**
32. **        try {**
33. **            Class.forName(driver);**
34. **        } catch (ClassNotFoundException e) {**
35. **            logger.fatal("找不到数据库驱动类"+driver,e);**
36. **        }**
37. **        // 初始化pool**
38. **        pool=new LinkedList<Connection>();**
39. **        // 创建5个链接对象**
40. **        for (int i = 0; i <initSize ; i++) {**
41. **            Connection connection = initConnection();**
42. **            if(null != connection){**
43. **                pool.add(connection);**
44. **                logger.info("初始化连接"+connection.hashCode()+"放入连接池");**
45. **            }**
46. **        }**
47. **    }**
48. **    // 私有的初始化一个链接对象的方法**
49. **    private static Connection initConnection(){**
50. **        try {**
51. **            return DriverManager.getConnection(url,user,password);**
52. **        } catch (SQLException e) {**
53. **            logger.fatal("初始化连接异常",e);**
54. **        }**
55. **        return null;**
56. **    }**
57. **    // 共有的向外界提供链接对象的**
58. **    public static Connection getConnection(){**
59. **        Connection connection =null;**
60. **        if(pool.size()>0){**
61. **            connection= pool.removeFirst();// 移除集合中的第一个元素**
62. **            logger.info("连接池中还有连接:"+connection.hashCode());**
63. **        }else{**
64. **            connection = initConnection();**
65. **            logger.info("连接池空,创建新连接:"+connection.hashCode());**
66. **        }**
67. **        return connection;**
68. **    }**
69. **    // 共有的向连接池归还连接对象的方法**
70. **    public static void returnConnection(Connection connection){**
71. **        if(null != connection){**
72. **            try {**
73. **                if(!connection.isClosed()){**
74. **                    if(pool.size()<maxSize){**
75. **                        try {**
76. **                            connection.setAutoCommit(true);// 调整事务状态**
77. **                           
    logger.debug("设置连接:"+connection.hashCode()+"自动提交为true");**
78. **                        } catch (SQLException e) {**
79. **                            e.printStackTrace();**
80. **                        }**
81. **                        pool.addLast(connection);**
82. **                        logger.info("连接池未满,归还连接:"+connection.hashCode());**
83. **                    }else{**
84. **                        try {**
85. **                            connection.close();**
86. **                           logger.info("连接池满了,关闭连接:"+connection.hashCode());**
87. **                        } catch (SQLException e) {**
88. **                            e.printStackTrace();**
89. **                        }**
90. **                    }**
91. **                }else{**
92. **                   logger.info("连接:"+connection.hashCode()+"已经关闭,无需归还");**
93. **                }**
94. **            } catch (SQLException e) {**
95. **                e.printStackTrace();**
96. **            }**
97. **        }else{**
98. **           logger.warn("传入的连接为null,不可归还");**
99. **        }**
100. **    }**
101. **}**

** **

**
**






------------------------------------------------------------

