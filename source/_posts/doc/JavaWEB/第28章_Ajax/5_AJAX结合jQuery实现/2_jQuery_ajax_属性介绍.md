
# 2_jQuery_ajax_属性介绍

###  jQuery.ajax()属性详解 

$.ajax()方法中有很多属性可以供我们使用,其中很多属性都有默认值,那么这些属性都有哪些,处理的是什么事情?接下来给大家一一介绍一下 

**1.url:**
要求为String类型的参数，（默认为当前页地址）发送请求的地址。 

**2.type:** 

要求为String类型的参数，请求方式（post或get）默认为get。注意其他http请求方法，例如put和delete也可以使用，但仅部分浏览器支持。 

**3.timeout:** 

要求为Number类型的参数，设置请求超时时间（毫秒）。此设置将覆盖$.ajaxSetup()方法的全局设置。 

**4.async:** 

要求为Boolean类型的参数，默认设置为true，所有请求均为异步请求。如果需要发送同步请求，请将此选项设置为false。注意，同步请求将锁住浏览器，用户其他操作必须等待请求完成才可以执行。
**5.cache:** 

要求为Boolean类型的参数，默认为true（当dataType为script时，默认为false），设置为false将不会从浏览器缓存中加载请求信息。 

**6.data:** 

要求为Object或String类型的参数，发送到服务器的数据。如果已经不是字符串，将自动转换为字符串格式。get请求中将附加在url后。防止这种自动转换，可以查看 
processData选项。对象必须为key/value格式，例如{foo1:"bar1",foo2:"bar2"}转换为&foo1=bar1&foo2=bar2
。如果是数组，JQuery将自动为不同值对应同一个名称。例如{foo:["bar1","bar2"]}转换为&foo=bar1&foo=bar2。 

**7.dataType:** 

要求为String类型的参数，预期服务器返回的数据类型。如果不指定，JQuery将自动根据http包mime信息返回responseXML或responseText
，并作为回调函数参数传递。可用的类型如下： 

xml：返回XML文档，可用JQuery处理。 

html：返回纯文本HTML信息；包含的script标签会在插入DOM时执行。 

script：返回纯文本JavaScript代码。不会自动缓存结果。除非设置了cache参数。注意在远程请求时（不在同一个域下），所有post请求都将转为get
请求。 

json：返回JSON数据。 

jsonp：JSONP格式。使用JSONP形式调用函数时，例如myurl?callback=?，JQuery将自动替换后一个“?”为正确的函数名，以执行回调函数。
text：返回纯文本字符串。 

**8.beforeSend：** 

要求为Function类型的参数，发送请求前可以修改XMLHttpRequest对象的函数，例如添加自定义HTTP头。在beforeSend中如果返回false
可以取消本次ajax请求。   


|                                                                                                   |XMLHttpRequest对象是惟一的参数。
  function(XMLHttpRequest){
       this; //调用本次ajax请求时传递的options参数
  }     |

**9.complete：** 

要求为Function类型的参数，请求完成后调用的回调函数（请求成功或失败时均调用）。参数：XMLHttpRequest对象和一个描述成功请求类型的字符串。 
 


|                                                                                |function(XMLHttpRequest, textStatus){
  this; //调用本次ajax请求时传递的options参数         |}                                                                               |

**10.success：** 

要求为Function类型的参数，请求成功后调用的回调函数，有两个参数。
(1)由服务器返回，并根据dataType参数进行处理后的数据。
(2)描述状态的字符串。
  


|                                                                                                            |function(data, textStatus){
  //data可能是xmlDoc、jsonObj、html、text等等
  this; //调用本次ajax请求时传递的options参数         |}                                                                                                           |

**11.error:** 

要求为Function类型的参数，请求失败时被调用的函数。该函数有3个参数，即XMLHttpRequest对象、错误信息、捕获的错误对象(可选)。ajax事件函数如下：
  


|                                                                                                                                       |function(XMLHttpRequest, textStatus, errorThrown){
  //通常情况下textStatus和errorThrown只有其中一个包含信息
  this; //调用本次ajax请求时传递的options参数         |}                                                                                                                                      |

**12.contentType：** 

要求为String类型的参数，当发送信息至服务器时，内容编码类型默认为"application/x-www-form-urlencoded"。该默认值适合大多数应用场合。
**13.dataFilter：** 

要求为Function类型的参数，给Ajax返回的原始数据进行预处理的函数。提供data和type两个参数。data是Ajax返回的原始数据，type是调用jQuery.ajax
时提供的dataType参数。函数返回的值将由jQuery进一步处理。

  


|                                                           |function(data, type){
  //返回处理后的数据
   return data;
  }     |

**14.global：** 

要求为Boolean类型的参数，默认为true。表示是否触发全局ajax事件。设置为false将不会触发全局ajax事件，ajaxStart或ajaxStop可用于控制各种
ajax事件。 

**15.ifModified：** 

要求为Boolean类型的参数，默认为false。仅在服务器数据改变时获取新数据。服务器数据改变判断的依据是Last-Modified头信息。默认值是false
，即忽略头信息。 

**16.jsonp：** 

要求为String类型的参数，在一个jsonp请求中重写回调函数的名字。该值用来替代在"callback=?"这种GET或POST请求中URL参数里的"callback"
部分，例如{jsonp:'onJsonPLoad'}会导致将"onJsonPLoad=?"传给服务器。 

**17.username：** 

要求为String类型的参数，用于响应HTTP访问认证请求的用户名。 

**18.password：** 

要求为String类型的参数，用于响应HTTP访问认证请求的密码。 

**19.processData：** 

要求为Boolean类型的参数，默认为true。默认情况下，发送的数据将被转换为对象（从技术角度来讲并非字符串）以配合默认内容类型"application/x-www-form-urlencoded"
。如果要发送DOM树信息或者其他不希望转换的信息，请设置为false。 

**20.scriptCharset：** 

要求为String类型的参数，只有当请求时dataType为"jsonp"或者"script"，并且type是GET时才会用于强制修改字符集(charset)。通常在本地和远程的内容编码不同时使用。
**一个ajax方法中,可用的属性和方法大致如下**   


|                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |<script>
  
  
      function testAjax(){
         $.ajax({
             url:"servlet1",
             /*post get  部分浏览器可使用put delete*/
             type:"get",
             /*请求超时的时间设置*/
             timeout:2000,
             /*是否发送异步请求,默认值为true,如需同步请求,改为false*/
             async:true,
             /*是否从浏览器的缓存中加载信息,默认为true,false则不读取浏览器缓存*/
             cache:true,
             /*向服务器发送的数据,可以是key/value格式,也可以是对象格式
             * get方式下,会将信息附加在url后,如果数据不是字符串,会转换成字符串格式
             * */
             data:{username:"bjmsb",password:"bjmsb"},
             /*
             * 默认值为true 默认情况下,发送的数据将被转换为对象以配合
             *   content-type:application/x-www-form-urlencoded
             * 如果发送信息不希望被转换,设置为false即可
             * */
             proccessData:true,
             /*发送到服务器的数据为String类型时,默认值为
             *   application/x-www-form-urlencoded
             * 该值适合大多数应用场景
             * */
             contentType:"application/x-www-form-urlencoded",
              /*
              * 预期服务器返回值类型,
              * 如果不指定 jQuery根据http响应mime信息返回xml或者text
              * 并作为返回值传递,可选类型如下
              * xml 返回xml数据(基本淘汰)
              * html:返回纯文本HTML信息
              * script:返回JS脚本,
              * json:返回json数据
              * jsonp:jsonp格式
              * text:返回纯文本,也是默认格式
              * */
             dataType:"json",
             /*
             * 指定跨域回调函数名
             * */
             //jsonp:"fun1",
  
             /*只有当请求参数为dataType为jsonp或者script,并且是get方式请求时
             * 才能强制修改字符集,通常在跨域编码不同时使用
             * */
            //  scriptCharset:"utf-8",
  
             beforeSend:function(XMLHttpRequest){
               /*
                * 请求发送前可以通过该方法修改XMLHttpRequest对象函数
                * 如听见请求头
                * 如果该方法返回false,则会取消ajax请求
                * */
             },
             success:function(data,textStatus){
                 /*
                 *一般请求成功后会调用的函数,有两个可选参数
                 * data,数据 根据dataType的配置处理之后的数据 可能是xml text json 等
                 * testStatus ,描述响应状态的字符串
                 *  */
             },
             error:function(XMLHttpRequest,textStatus,errorThrown){
                 /*
                 * 请求失败时调用的函数,可选参数有
                 * XMLHttpRequest对象
                 * 错误信息
                 * 捕获的异常对象
                 * */
             },
             complete:function(XMLHttpRequest,textStatus){
                 /*
                 * 无论请求是否成功都睡调用的回调函数
                 * 可选参数有
                 * XMLHttpRequest对象
                 * textStatus 描述成功请求的类型的字符串
                 * */
             },
             dataFilter:function(data,type){
                 /*
                 * 数据过滤方法
                 * 给Ajax返回的原始数据进行预处理的函数。
                 * 提供data和type两个参数。
                 * data是Ajax返回的原始数据，
                 * type是调用jQuery.ajax时提供的dataType参数。
                 * 函数返回的值将由jQuery进一步处理
                 * */
             }
  
         })
      }
  
  
  </script>         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

注意: 

ajax异步提交的可选属性和方法较多,实际研发我们没必要写这么多,一般可以使用默认值的属性就可以省略不写,一些业务逻辑或者功能上不需要的方法也可以省略不写,由于属性太多
,针对于一些特殊情况,jQuery也给我们提供了一些专用的方法,这样可以简化$.ajax的写法,每一种简化写法都相当于已经指定了$.ajax一些属性的值. 



------------------------------------------------------------

