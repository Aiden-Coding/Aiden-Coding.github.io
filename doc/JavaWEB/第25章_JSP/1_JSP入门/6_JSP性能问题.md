﻿
# 6_JSP性能问题

#### JSP的性能问题 

有人都会认为JSP的执行性能会和Servlet相差很多，其实执行性能上的差别只在第一次的执行。因为JSP在执行第一次后，会被编译成Servlet的类文件，即.class
，当再重复调用执行时，就直接执行第一次所产生的Servlet,而不再重新把JSP编译成Servelt。除了第一次的编译会花较久的时间之外，之后JSP和同等功能的
Servlet的执行速度就几乎相同了。 

JSP慢的原因不仅仅是第一次请求需要进行转译和编译,而是因为JSP作为一种动态资源,本质上就是Servlet,它是需要运行代码才会生成资源,和HTML本身资源已经存在,直接返回,着本质上的差异,另外,JSP转译之后,内部通过大量IO流形式发送页面内容,IO流本身是一种重量级操作,是比较消耗资源的



 在前后端分离时代,JSP作为一种前后端混合技术就不在适用了,但是JSP和Servlet关联比较紧密,所以学习Servlet技术一定要了解一些JSP技术.作为一种软件行业的从业人员
,JSP技术是一种基础性技术,是我们学习后面的知识的一种知识积累.JSP技术在某些独特的领域和在一些特定的需求下,还是有存在的必要的,如很多政府和事业单位的项目中就存在大量的
JSP应用情况.在我们没有学习更加多的页面静态化和前后端分离技术之前,我们还是要借助JSP技术作为数据展现的一种处理手段,从学习JSP到从JSP中向更高的技术进化需要一个过程
. 



------------------------------------------------------------

