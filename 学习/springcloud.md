# 单词读法

eureka   有瑞卡	

nacos   呐蔻丝

consul   kang3  so

ribbon  rui1  本

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

# 常用命令
