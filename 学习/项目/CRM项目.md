其实localhost是不好的，他就是host文件中127.0.0.1的一个映射

简体中文，操作系统默认编码---GBK

web客户端都是请求驱动的

idea 对HTML采用的编码格式是ISO  对jsp采用的是UTF-8

CRM项目的核心业务：
    系统管理功能：不是直接处理业务数据，为了保证业务管理的功能正常安全运行而设计的功能。
                  用户登录,安全退出,登录验证等
		  给超级管理员，开发和运维人员使用。
    业务管理功能：处理业务数据
                  市场活动：市场部，设计市场活动营销活动
		  线索：销售部(初级销售),增加线索
		  客户和联系人：销售部(高级销售),有效地区分和跟踪客户和联系人.
                  交易：销售部(高级销售),更好地区分和统计交易的各个阶段。
		  售后回访：客服部,妥善安排售后回访。主动提醒。
                  统计图表：管理层,统计交易表中各个阶段数据量。

   pageContext:用来在同一个页面的不同标签之间传递数据。
   request：在同一个请求过程中间传递数据。
   session: 同一个浏览器窗口的不同请求之间传递数据。
   application:所有用户共享的数据，并且长久频繁使用的数据。

①：拦截器是基于java的反射机制的，而过滤器是基于函数的回调。
②：拦截器不依赖于servlet容器，而过滤器依赖于servlet容器。
③：拦截器只对action请求起作用，而过滤器则可以对几乎所有的请求起作用。
④：拦截器可以访问action上下文、值、栈里面的对象，而过滤器不可以。
⑤：在action的生命周期中，拦截器可以多次被调用，而过滤器只能在容器初始化时被调用一次。
⑥：拦截器可以获取IOC容器中的各个bean，而过滤器不行，这点很重要，在拦截器里注入一个service，可以调用业务逻辑。


```
 拦截器只会拦截访问的控制器方法， 如果访问的是jsp/html/css/image/js是不会进行拦截的
```