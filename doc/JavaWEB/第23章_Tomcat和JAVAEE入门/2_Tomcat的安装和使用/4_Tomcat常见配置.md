
# 4_Tomcat常见配置

#### Tomcat配置文件介绍 

Tomcat 的配置文件由4个xml组成，分别是 context.xml、web.xml、server.xml、tomcat-users.xml。每个文件都有自己的功能与配置方法。
**context.xml** 

Context.xml 是 Tomcat 公用的环境配置。 Tomcat 服务器会定时去扫描这个文件。一旦发现文件被修改（时间戳改变了），就会自动重新加载这个文件，而不需要重启服务器 。
**web.xml** 

Web应用程序描述文件，都是关于是Web应用程序的配置文件。所有Web应用的 web.xml 文件的父文件。 

**server.xml** 

是 tomcat 服务器的核心配置文件，server.xml的每一个元素都对应了 tomcat中的一个组件，通过对xml中元素的配置，实现对 tomcat中的各个组件和端口的配置。
**tomcat-users.xml** 

配置访问Tomcat的用户以及角色的配置文件。



#### 解决控制台乱码 

控制台产生乱码的原因是在Tomcat在输出日志中使用的是UTF-8编码，而我们中文的Windows操作系统使用的是GBK编码。由于编码格式不统一，所以出现了乱码。
解决方式： 

修改conf目录中的logging.properties文件重新指定的编码方式。如果还是不行,那么 就删除该行即可   


|                                                      |java.util.logging.ConsoleHandler.encoding   = GBK     |





#### 
修改Tomcat监听端口 

Tomcat默认监听端口为8080。可以通过修改server.xml文件来改变Tomcat的监听端口。   


|                                                                                                                                        |<Connector   port="8080" protocol="HTTP/1.1"                                                                                            |                 connectionTimeout="20000"                                                                                              |               redirectPort="8443"   />                                                                                                 |



80是http协议默认的端口号:在http:1.1中,如果不写端口号那么默认端口号就是80



#### 
配置Tomcat并发数 

Tomcat的最大并发数是可以配置的，实际运用中，最大并发数与硬件性能和CPU数量都有很大关系的。更好的硬件，更多的处理器都会使Tomcat支持更多的并发。

    这个并发能力还与应用的逻辑密切相关，如果逻辑很复杂需要大量的计算，那并发能力势必会下降。如果每个请求都含有很多的数据库操作，那么对于数据库的性能也是非常高的。
对于单台数据库服务器来说，允许客户端的连接数量是有限制的。并发能力问题涉及整个系统架构和业务逻辑、系统环境不同、Tomcat版本不同、JDK版本不同、以及修改的设定参数不同。并发量的差异还是满大的。并发数设置参数有如下几个
maxThreads="1000" 

最大并发数  

minSpareThreads="100" 

初始化时创建的线程数 

maxSpareThreads="500" 

一旦创建的线程超过这个值，Tomcat就会关闭不再需要的socket线程。 

acceptCount="700" 

指定当所有可以使用的处理请求的线程数都被使用时，可以放到处理队列中的请求数，超过这个数的请求将不予处理 

配置实例：   


|                                                                                                                                                                                        |<Connector port="8080" protocol="HTTP/1.1"    minSpareThreads="100"  maxSpareThreads="500"   maxThreads="1000" acceptCount="700" connectionTimeout="20000" redirectPort="8443"   />     |

  

#### 配置Tomcat Manager 

**什么是Tomcat Manager** 

Tomcat Manager是Tomcat自带的、用于对Tomcat自身以及部署在Tomcat上的应用进行管理的web应用。默认情况下，Tomcat
Manager是处于禁用状态的。准确的说，Tomcat Manager需要以用户角色进行登录并授权才能使用相应的功能，不过Tomcat并没有配置任何默认的用户，因此我们需要先进行用户配置后才能使用
Tomcat Manager。 

**配置Tomcat Manager的访问用户** 

Tomcat Manager中没有默认用户，我们需要在tomcat-users.xml文件配置。Tomcat Manager的用户配置需要配置两个部分：角色配置、用户名及密码配置。
**Tomcat Manager中的角色分类** 

manager-gui角色： 

允许访问HTML GUI和状态页面(即URL路径为/manager/html/*) 

manager-script角色： 

允许访问文本界面和状态页面(即URL路径为/manager/text/*) 

manager-jmx角色： 

允许访问JMX代理和状态页面(即URL路径为/manager/jmxproxy/*) 

manager- status角色： 

仅允许访问状态页面(即URL路径为/manager/status/*) 

**配置用户及角色**   


|                                                                                                                                                                                                                                                                                                                                                                             |  <role   rolename="manager-gui"/>                                                                                                                                                                                                                                                                                                                                           |  <role   rolename="manager-script"/>                                                                                                                                                                                                                                                                                                                                        |  <role   rolename="manager-jmx"/>                                                                                                                                                                                                                                                                                                                                           |  <role rolename="manager-status"/>                                                                                                                                                                                                                                                                                                                                          |  <role   rolename="admin-gui"/>                                                                                                                                                                                                                                                                                                                                             |  <role   rolename="admin-script"/>                                                                                                                                                                                                                                                                                                                                          |  <user username="tomcat"   password="tomcat"                                                                                                                                                                                                                                                                                                                                | roles="manager-gui,manager-script,manager-jmx,manager-status,admin-gui,admin-script"/>                                                                                                                                                                                                                                                                                      |
























------------------------------------------------------------

