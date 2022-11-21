# 单词读法

eureka   有瑞卡	

nacos   呐蔻丝

consul   kang3  so

ribbon  rui1  本

Feign  fun

openFeign  open非嗯 

 hystrix     嗨死chui4 个死 

sentinel   森ten4 no

gateway   get way

nacos  呐蔻丝

apollo  阿波罗

CAP 

# 笔记

spring cloud是一个全家桶![image-20220830161714882](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830161714882.png)

![image-20220830161946561](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830161946561.png)

![image-20220830174300831](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830174300831.png)

alibaba自己的Nacos,可以兼容两种远程调用协议

每个服务单独的数据库从根源上杜绝了耦合的业务。

使用resttemplate来模仿http的远程调用![image-20220830194439509](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830194439509.png)

一个服务可以同时是消费者也可以是提供者

eureka也是一个微服务，也要把自己注册进去，方便之后多个eureka一起工作，为了服务的注册才配置的信息![image-20220830202152686](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830202152686.png)

这是一个进程，上面加上注解![image-20220830202530248](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830202530248.png)

搭建注册中心三步走：引入、配置，注解和![image-20220830202943811](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830202943811.png)

注册服务：![image-20220830202854960](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830202854960.png)

一个服务我们可能需要多个实例![image-20220830203306032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830203306032.png)

。yml里面配置eureka的地址就是注册

![image-20220830203603373](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830203603373.png)

给resttemplate加上了注解，让他能够负载均衡，我们的请求没有具体地址，只有想要的服务![image-20220830210332693](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830210332693.png)

![image-20220830210640991](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830210640991.png)

![image-20220831084338538](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831084338538.png)这个第二个是针对某一个微服务规则的

![image-20220831085655038](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831085655038.png)

  

依赖里面不能同时有eureka和nacos，nacos没有一个eureka启动模块，他就是一个软件，打开就能用，我们找到他的端口，直接注册

nacos的分级存储模型，两个服务的调用，配置在同一个集群，会本地集群访问，否则夸集群访问会warring

nacos界面可以配权重，不同权重可以让我们一个一个的更新服务器。还能放少数用户进来进行测试

命名空间：在相同的空间下才可以互相访问。discoverd:namespace : namespaceid    

nacos的配置管理，可以热更新，配置里面写的主要是一些开关配置，比如不同的业务模式或者模板  data format之类的。我们有一个nacos的配置文件之后，服务端引入依赖，然后配置文件里面写出去哪里请求。之后我们在

fegin继承了rebbin  自动实现了负载均衡，![image-20220831160428722](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831160428722.png)就是告诉这个服务去哪里可以找到服务。这里声明了一个路径，userservice / user/{id},调用的时候根据这个方法UserClient.findById就可以直接根据这个的路径去userservice(有负载均衡)/user/{id}去找请求了。这种基于注解的方法，想要请求一个东西不需要繁琐的配置路径，直接声明一个方法，并指明那个服务的那个方法就可以了。加入的@EnableFeginClient就像是一个开关；；；；就是让消费者基于这个信息去发送一个请求![image-20220831162259865](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831162259865.png)这两个必须一样

![image-20220831162522143](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831162522143.png)

getaway   可以把访问存在网关

通过适配器模式，每个过滤器是差不多的![image-20220831173525215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831173525215.png)

Docker

操作系统是将微指令封装成函数，然后调用，不同的操作系统尽管内核相同，但是函数库不同，所以不通用，我们是基于函数开发的沙箱机制![image-20220831191944221](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831191944221.png)

docker可以直接调用内核![image-20220831193034142](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220831193034142.png)

使用分卷后可以把文件从容器中拿出来，用高级编辑器去编辑非常好用

ES就是一个将词条作为索引的搜索引擎，进行两次搜索，先根据词条找到ID之后根据ID找到文档；正向索引是先找ID之后从这个ID的文档里面找词条，而倒序索引是先找词条，然后根据词条去找ID，找到文档

![image-20220903150543939](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220903150543939.png)

MQ解耦合![image-20220903150707015](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220903150707015.png)

雪崩：微服务中，很多东西是相互依靠的，一个服务崩了后面依靠他的也崩了，所以叫雪崩；依赖他的和他依赖的都会崩掉![image-20220903160354592](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220903160354592.png)



# 常用命令



# 问题

jdk17启动sentinal失败

异常是由Java 9及以上版本中引入的Java Platform Module System引起的，特别是强封装的实现。
它仅在特定条件下允许access，最突出的条件是:

- 类型必须是公共的
- 必须导出拥有的软件包
- 更改启动命令，打开特定的包装进行反射：
  `java --add-opens java.base/java.lang=ALL-UNNAMED -jar sentinel-dashboard-1.8.1.jar`
