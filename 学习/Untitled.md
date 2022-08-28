jsp 其实是后端技术，（动态网页技术）他是运行在后台的，他的运行结果是网页，在浏览器上显示

service 没有成员变量，所以像单例类一样，一个就够用了

Spring 是一个框架，是一个半成品的软件。有 20 个模块组成。它是一个容器管理对象， 容器是装东西的，Spring 容器不装文本，数字。装的是对象。Spring 是存储对象的容器。

Spring 提供了 Ioc 控制反转，由容器管理对象，对象的依赖关系。原来在程序代码中的对象创建方式，现在由容器完成。对象之间的依赖解耦合。

***\*ApplicationContext 容器，会在容器对象初始化时，将其中的所有对象一次性全部装配好。\****以后代码中若要使用到这些对象，只需从内存中直接获取即可。执行效率较高。但占用内存。

当配置文件中被调用者 bean 的 id 值与代码中调用者 bean 类的属性名相同时，可使用byName 方式，让容器自动将被调用者 bean 注入给调用者 bean。容器是通过调用者的 bean类的属性名与配置文件的被调用者 bean 的 id 进行比较而实现自动注入的。@AutoWrite Aaaservice和 <id = aaaservice>

依赖注入：DI(Dependency Injection)，对于 DI 使用注解，将不再需要在 Spring 配置文件中声明bean 实例。Spring 中使用注解， 需要在原有 Spring 运行环境基础上再做一些改变。需要在 Spring 配置文件中配置组件扫描器，用于在指定的基本包中扫描注解。

#### **（1）*****\*创建对象的注解\****

@Component :创建所有对象都可以使用此注解,除了控制器,业务逻辑层,数据访问层的对象

 @Controller:创建控制器层的对象,此对象可以接收用户请求,返回处理结果

 @Service:创建业务逻辑层的对象,此对象可施事务控制,向上给控制器返回数据,向下调用数据访问层

 @Repository:创建数据访问层的对象 ,对数据库中的数据进行增删改查操作

对象赋值：@Autowired:给引用类型按类型注入

 				 @Qualifier:给引用类型按名称注入

，@Controller 注解创建的对象**可以作为处理器接收用户的请求。**@Repository，@Service，@Controller 是对@Component 注解的细化，标注不同层的对象。即持久层对象，业务层对象，控制层对象。

**@Component 不指定 value 属性，bean 的 id 是类名的首字母小写。**

![image-20220705184420665](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220705184420665.png)

***\*如果可注入的类型多于一个,则按名称进行二次匹配.如果有匹配到则注入,如果没有匹配到,则报错\****。![image-20220705184637468](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220705184637468.png)



