- https://www.baidu.com/ （网址）
- www.baidu.com 是一个域名
- 在浏览器地址栏上输入域名，回车之后，域名解析器会将域名解析出来一个具体的IP地址和端口号等。

- 一个WEB系统的通信原理？通信步骤：
  - 第一步：用户输入网址（URL）
  - 第二步：域名解析器进行域名解析：http://110.242.68.3:80/index.html
  - 第三步：浏览器软件在网络中搜索110.242.68.3这一台主机，直到找到这台主机。
  - 第四步：定位110.242.68.3这台主机上的服务器软件，因为是80端口，可以很轻松的定位到80端口对应的服务器软件。
  - 第五步：**80端口对应的服务器软件得知浏览器想要的资源名是：index.html**
  - 第六步：服务器软件找到index.html文件，并且将index.html文件中的内容直接输出响应到浏览器上。
  - 第七步：浏览器接收到来自服务器的代码（HTML CSS JS）
  - 第八步：浏览器渲染，执行HTML CSS JS代码，展示效果。
- 

应用服务器和WEB服务器的关系？

- **应用服务器实现了JavaEE的所有规范。(JavaEE有13个不同的规范。)**
- **WEB服务器只实现了JavaEE中的Servlet + JSP两个核心的规范。**
- 通过这个讲解说明了：应用服务器是包含WEB服务器的。
- 用过JBOSS服务器的同学应该很清楚，JBOSS中内嵌了一个Tomcat服务器

- tomcat还有另外一个名字：catalina（catalina是美国的一个岛屿，风景秀丽，据说作者是在这个风景秀丽的小岛上开发了一个轻量级的WEB服务器，体积小，运行速度快，因此tomcat又被称为catalina）
- tomcat的logo是一只公猫（寓意表示Tomcat服务器是轻巧的，小巧的，果然，体积小，运行速度快，只实现了Servlet+JSP规范）

- tomcat是java语言写的。
- tomcat服务器要想运行，必须先又jre（Java的运行时环境）

bin目录下有一个文件：startup.bat,通过它可以启动Tomcat服务器。

- xxx.bat文件是个什么文件？bat文件是windows操作系统专用的，bat文件是批处理文件，这种文件中可以编写大量的windows的dos命令，然后执行bat文件就相当于批量的执行dos命令。

- startup.sh，这个文件在windows当中无法执行，在Linux环境当中可以使用。在Linux环境下能够执行的是shell命令，大量的shell命令编写在shell文件当中，然后执行这个shell文件可以批量的执行shell命令。

- tomcat服务器提供了bat和sh文件，说明了这个tomcat服务器的通用性。

- 分析startup.bat文件得出，执行这个命令，实际上最后是执行：catalina.bat文件。

  tomcat服务器就是Java语言写的，既然是java语言写的，那么启动Tomcat服务器就是执行main方法。

关于Tomcat服务器的目录

lib ：这个目录是Tomcat服务器的核心程序目录，因为Tomcat服务器是Java语言编写的，这里的jar包里面都是class文件

webapps：这个目录当中就是用来存放大量的webapp（web application：web应用）

- 第一步：找到CATALINA_HOME\webapps目录

  - 因为所有的webapp要放到webapps目录下。（没有为什么，这是Tomcat服务器的要求。如果不放到这里，Tomcat服务器找不到你的应用。）
- 第二步：在CATALINA_HOME\webapps目录下新建一个子目录，起名：oa

  - 这个目录名oa就是你这个webapp的名字。
- 第三步：在oa目录下新建资源文件，例如：index.html

  - 编写index.html文件的内容。
- 第四步：启动Tomcat服务器
- 第五步：打开浏览器，在浏览器地址栏上输入这样的URL：

- http://127.0.0.1:8080/oa/index.html    //oa是软件名

Servlet规范的作用是什么？

- WEB Server   和   webapp解耦合。

- 第二步：在webapp的根下新建一个目录：WEB-INF

  - 注意：这个目录的名字是Servlet规范中规定的，必须全部大写，必须一模一样。必须的必须。

- 第三步：在WEB-INF目录下新建一个目录：classes

  - 注意：这个目录的名字必须是全部小写的classes。这也是Servlet规范中规定的。另外这个目录下一定存放的是Java程序编译之后的class文件（这里存放的是字节码文件）。

- 第四步：在WEB-INF目录下新建一个目录：lib

  - 注意：这个目录不是必须的。但如果一个webapp需要第三方的jar包的话，这个jar包要放到这个lib目录下，这个目录的名字也不能随意编写，必须是全部小写的lib。例如java语言连接数据库需要数据库的驱动jar包。那么这个jar包就一定要放到lib目录下。这Servlet规范中规定的。

- 第五步：在WEB-INF目录下新建一个文件：web.xml

  - 注意：这个文件是必须的，这个文件名必须叫做web.xml。这个文件必须放在这里。一个合法的webapp，web.xml文件是必须的，这个web.xml文件就是一个配置文件，在这个配置文件中描述了请求路径和Servlet类之间的对照关系。

Servlet接口不在JDK当中。（因为Servlet不是JavaSE了。Servlet属于JavaEE，是另外的一套类库。）

在web.xml文件中**注册Servlet类。**

```xml
<!--任何一个servlet都对应一个servlet-mapping -->
<servlet>
	<servlet-name>fdsafdsagfdsafdsa</servlet-name>
	<!--这个位置必须是带有包名的全限定类名-->
	<servlet-class>com.bjpowernode.servlet.HelloServlet</servlet-class>
</servlet>
<!--servlet映射信息-->
	<servlet-mapping>
		<!--这个也是随便的，不过这里写的内容要和上面的一样。-->
		<servlet-name>fdsafdsagfdsafdsa</servlet-name>
		<!--这里需要一个路径-->
		<!--这个路径唯一的要求是必须以 / 开始-->
		<!--当前这个路径可以随便写-->
		<url-pattern>/fdsa/fd/saf/d/sa/fd/sa/fd</url-pattern>
	</servlet-mapping>
```

非常重要：html页面只能放到WEB-INF目录外面。

以后不需要我们编写main方法了。tomcat服务器负责调用main方法，Tomcat服务器启动的时候执行的就是main方法。我们javaweb程序员只需要编写Servlet接口的实现类，然后将其注册到web.xml文件中，即可。

webapproot
     |------WEB-INF
     		  |------classes(存放字节码)
     		  |------lib(第三方jar包)
     		  |------web.xml(注册Servlet)
     |------html
     |------css
     |------javascript
     |------image
     ....

浏览器发送请求，到最终服务器调用Servlet中的方法，是怎样的一个过程？（以下这个过程描述的很粗糙。其中还有很多步骤我省略了。）

- 用户输入URL，或者直接点击超链接：http://127.0.0.1:8080/crm/fdsa/fd/saf/d/sa/fd/sa/fd  
- 然后Tomcat服务器接收到请求，截取路径：/crm/fdsa/fd/saf/d/sa/fd/sa/fd  
- Tomcat服务器找到crm项目
- Tomcat服务器在web.xml文件中查找/fdsa/fd/saf/d/sa/fd/sa/fd  对应的Servlet是：com.bjpowernode.servlet.HelloServlet
- Tomcat服务器通过反射机制，创建com.bjpowernode.servlet.HelloServlet的对象。
- Tomcat服务器调用com.bjpowernode.servlet.HelloServlet对象的service方法。

- JavaEE目前最高版本是 JavaEE8
- JavaEE被Oracle捐献了，Oracle将JavaEE规范捐献给Apache了。
- Apache把JavaEE换名了，以后不叫JavaEE了，以后叫做 jakarta EE。
- 以后没有JavaEE了。以后都叫做Jakarta EE。

需要注意的：在IDEA工具中根据Web Application模板生成的目录中有一个web目录，这个目录就代表webapp的根

在web.xml文件中完成StudentServlet类的注册。（请求路径和Servlet之间对应起来）

- Tomcat服务器通常我们又称为：WEB容器。（这个叫法你要知道【WEB Container】）
- WEB容器来管理Servlet对象的死活。

- 我们自己new的Servlet对象是不受WEB容器管理的。
- WEB容器创建的Servlet对象，这些Servlet对象都会被放到一个集合当中（HashMap），只有放到这个HashMap集合中的Servlet才能够被WEB容器管理，自己new的Servlet对象不会被WEB容器管理。（自己new的Servlet对象不在容器当中）
- web容器底层应该有一个HashMap这样的集合，在这个集合当中存储了Servlet对象和请求路径之间的关系

用户在发送第二次，或者第三次，或者第四次请求的时候，Servlet对象并没有新建，还是使用之前创建好的Servlet对象，直接调用该Servlet对象的service方法，这说明：

- 第一：Servlet对象是单例的（单实例的。但是要注意：Servlet对象是单实例的，但是Servlet类并不符合单例模式。我们称之为假单例。之所以单例是因为Servlet对象的创建我们javaweb程序员管不着，这个对象的创建只能是Tomcat来说了算，Tomcat只创建了一个，所以导致了单例，但是属于假单例。**真单例模式，构造方法是私有化的。**）

- - Servlet的destroy方法只被Tomcat服务器调用一次。
  - destroy方法是在什么时候被调用的？
    - 在服务器关闭的时候。
    - 因为服务器关闭的时候要销毁AServlet对象的内存。
    - 服务器在销毁AServlet对象内存之前，Tomcat服务器会自动调用AServlet对象的destroy方法。

- 

Servlet对象更像一个人的一生：

- Servlet的无参数构造方法执行：标志着你出生了。
- Servlet对象的init方法的执行：标志着你正在接受教育。
- Servlet对象的service方法的执行：标志着你已经开始工作了，已经开始为人类提供服务了。
- Servlet对象的destroy方法的执行：标志着临终。有什么遗言，抓紧的。要不然，来不及了。

通常在init方法当中做初始化操作，并且这个初始化操作只需要执行一次。例如：初始化数据库连接池，初始化线程池....

- Tomcat服务器调用Servlet对象的init方法的时候需要传一个ServletConfig对象的参数给init方法。

- ServletConfig接口的实现类是Tomcat服务器给实现的。（Tomcat服务器说的就是WEB服务器。）

- 只要在同一个webapp当中，只要在同一个应用当中，所有的Servlet对象都是共享同一个ServletContext对象的。

- ServletContext对象在服务器启动阶段创建，在服务器关闭的时候销毁。这就是ServletContext对象的生命周期。ServletContext对象是应用级对象。

```java
// ServletContext对象还有另一个名字：应用域（后面还有其他域，例如：请求域、会话域）

// 如果所有的用户共享一份数据，并且这个数据很少的被修改，并且这个数据量很少，可以将这些数据放到ServletContext这个应用域中
```

- 注意：以后我们编写Servlet类的时候，实际上是不会去直接继承GenericServlet类的，因为我们是B/S结构的系统，这种系统是基于HTTP超文本传输协议的，在Servlet规范当中，提供了一个类叫做HttpServlet，它是专门为HTTP协议准备的一个Servlet类。我们编写的Servlet类要继承HttpServlet。（HttpServlet是HTTP协议专用的。）使用HttpServlet处理HTTP协议更便捷。但是你需要直到它的继承结构：

  - ```
    jakarta.servlet.Servlet（接口）【爷爷】
    jakarta.servlet.GenericServlet implements Servlet（抽象类）【儿子】
    jakarta.servlet.http.HttpServlet extends GenericServlet（抽象类）【孙子】
    
    我们以后编写的Servlet要继承HttpServlet类。
    ```

  

什么是超文本？

- 超文本说的就是：不是普通文本，比如流媒体：声音、视频、图片等。
- HTTP协议支持：不但可以传送普通字符串，同样支持传递声音、视频、图片等流媒体信息。

- HTTP的请求协议包括：4部分

  - 请求行
  - 请求头
  - 空白行
  - 请求体

- HTTP请求协议的具体报文：GET请求

```http
GET /servlet05/getServlet?username=lucy&userpwd=1111 HTTP/1.1                           请求行
Host: localhost:8080                                                                    请求头
Connection: keep-alive
sec-ch-ua: "Google Chrome";v="95", "Chromium";v="95", ";Not A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.54 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost:8080/servlet05/index.html
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
                                                                                        空白行
                                                                                        请求体
```

```http
POST /servlet05/postServlet HTTP/1.1                                                  请求行
Host: localhost:8080                                                                  请求头
Connection: keep-alive
Content-Length: 25
Cache-Control: max-age=0
sec-ch-ua: "Google Chrome";v="95", "Chromium";v="95", ";Not A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost:8080
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.54 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost:8080/servlet05/index.html
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
                                                                                      空白行
username=lisi&userpwd=123                                                             请求体
```

请求行

- 包括三部分：
  - 第一部分：请求方式（7种）
    - get（常用的）
    - post（常用的）
    - delete
    - put
    - head
    - options
    - trace
  - 第二部分：URI
    - 什么是URI？ 统一资源标识符。代表网络中某个资源的名字。但是通过URI是无法定位资源的。
    - 什么是URL？统一资源定位符。代表网络中某个资源，同时，通过URL是可以定位到该资源的。
    - URI和URL什么关系，有什么区别？
      - URL包括URI
      - http://localhost:8080/servlet05/index.html 这是URL。
      - /servlet05/index.html 这是URI。
  - 第三部分：HTTP协议版本号

- 请求头

  - 请求的主机
  - 主机的端口
  - 浏览器信息
  - 平台信息
  - cookie等信息
  - ....

- 空白行

  - 空白行是用来区分“请求头”和“请求体”

- 请求体

  - 向服务器发送的具体数据。

- 

- HTTP的响应协议（S --> B）

  - HTTP的响应协议包括：4部分

    - 状态行
    - 响应头
    - 空白行
    - 响应体

怎么向服务器发送GET请求，怎么向服务器发送POST请求？

- 到目前为止，只有一种情况可以发送POST请求：使用form表单，并且form标签中的method属性值为：method="post"。
- 其他所有情况一律都是get请求：
  - 在浏览器地址栏上直接输入URL，敲回车，属于get请求。
  - 在浏览器上直接点击超链接，属于get请求。
  - 使用form表单提交数据时，form标签中没有写method属性，默认就是get
  - 或者使用form的时候，form标签中method属性值为：method="get"





- post请求可以发送任何类型的数据，包括普通字符串，流媒体等信息：视频、声音、图片。
- post请求可以发送大数据量，理论上没有长度限制。
- get请求在W3C中是这样说的：get请求比较适合从服务器端获取数据。
- post请求在W3C中是这样说的：post请求比较适合向服务器端传送数据。
- get请求是安全的。get请求是绝对安全的。为什么？因为get请求只是为了从服务器上获取数据。不会对服务器造成威胁。

post请求是危险的。为什么？因为post请求是向服务器提交数据，如果这些数据通过后门的方式进入到服务器当中，服务器是很危险的。另外post是为了提交数据，所以一般情况下拦截请求的时候，大部分会选择拦截（监听）post请求。

做文件上传，一定是post请求。要传的数据不是普通文本。

欢迎页可以是一个Servlet吗？

- 当然可以。

- 你不要多想，欢迎页就是一个资源，既然是一个资源，那么可以是静态资源，也可以是动态资源。

- 静态资源：index.html welcome.html .....

- 动态资源：Servlet类。

放在WEB-INF目录下的资源是受保护的。在浏览器上不能够通过路径直接访问。所以像HTML、CSS、JS、image等静态资源一定要放到WEB-INF目录之外。

request对象实际上又称为“请求域”对象。

- 应用域对象是什么？

  - ServletContext （Servlet上下文对象。）

两个servlet共享数据

可以将数据放到request域当中，然后AServlet转发到BServlet，保证AServlet和BServlet在同一次请求当中，这样就可以做到两个Servlet，或者多个Servlet共享同一份数据。

```java
// uri?username=zhangsan&userpwd=123&sex=1
String username = request.getParameter("username");

// 之前一定是执行过：request.setAttribute("name", new Object())
Object obj = request.getAttribute("name");

// 以上两个方法的区别是什么？
// 第一个方法：获取的是用户在浏览器上提交的数据。
// 第二个方法：获取的是请求域当中绑定的数据。
```

转发和重定向有什么区别？

- 代码上有什么区别？

  - 转发

    - ```java
      // 获取请求转发器对象
      RequestDispatcher dispatcher = request.getRequestDispatcher("/dept/list");
      // 调用请求转发器对象的forward方法完成转发
      dispatcher.forward(request, response);
      
      // 合并一行代码
      request.getRequestDispatcher("/dept/list").forward(request, response);
      // 转发的时候是一次请求，不管你转发了多少次。都是一次请求。
      // AServlet转发到BServlet，再转发到CServlet，再转发到DServlet，不管转发了多少次，都在同一个request当中。
      // 这是因为调用forward方法的时候，会将当前的request和response对象传递给下一个Servlet。
      ```

  - 重定向

    - ```java
      // 注意：路径上要加一个项目名。为什么？
      // 浏览器发送请求，请求路径上是需要添加项目名的。
      // 以下这一行代码会将请求路径“/oa/dept/list”发送给浏览器
      // 浏览器会自发的向服务器发送一次全新的请求：/oa/dept/list
      response.sendRedirect("/oa/dept/list");
      ```

      - - -

      - 形式上有什么区别？

        - 转发（一次请求）
          - 在浏览器地址栏上发送的请求是：http://localhost:8080/servlet10/a ，最终请求结束之后，浏览器地址栏上的地址还是这个。没变。，传递request  response
          - 、如果在上一个Servlet当中向request域当中绑定了数据，希望从下一个Servlet当中把request域里面的数据取出来，使用转发机制。
        - 重定向（两次请求）
          - 在浏览器地址栏上发送的请求是：http://localhost:8080/servlet10/a ，最终在浏览器地址栏上显示的地址是：http://localhost:8080/servlet10/b

一些不会经常变化修改的配置建议使用注解。一些可能会被修改的建议写到配置文件中。

类爆炸。（类的数量太大。）

- 在java的servlet规范当中，session对应的类名：HttpSession（jarkata.servlet.http.HttpSession）

- 什么是无状态：请求的时候，B和S是连接的，但是请求结束之后，连接就断了。为什么要这么做？HTTP协议为什么要设计成这样？因为这样的无状态协议，可以降低服务器的压力。请求的瞬间是连接的，请求结束之后，连接断开，这样服务器压力小。

request < session < application

HttpSession session = request.getSession();

session的实现原理：

- JSESSIONID=xxxxxx  这个是以Cookie的形式保存在浏览器的内存中的。浏览器只要关闭。这个cookie就没有了。
- session列表是一个Map，map的key是sessionid，map的value是session对象。
- 用户第一次请求，服务器生成session对象，同时生成id，将id发送给浏览器。
- 用户第二次请求，自动将浏览器内存中的id发送给服务器，服务器根据id查找session对象。
- 关闭浏览器，内存消失，cookie消失，sessionid消失，会话等同于结束。

cookie禁用了，session机制还能实现吗？

- 可以。需要使用URL重写机制。
- http://localhost:8080/servlet12/test/session;jsessionid=19D1C99560DCBF84839FA43D58F56E16
- URL重写机制会提高开发者的成本。开发人员在编写任何请求路径的时候，后面都要添加一个sessionid，给开发带来了很大的难度，很大的成本。所以大部分的网站都是这样设计的：你要是禁用cookie，你就别用了。

对于session关联的cookie来说，这个cookie是被保存在浏览器的“运行内存”当中。

cookie最终是保存在浏览器客户端上的。

- 可以保存在运行内存中。（浏览器只要关闭cookie就消失了。）
- 也可以保存在硬盘文件中。（永久保存。）

- cookie和session机制其实都是为了保存会话的状态。
- cookie是将会话的状态保存在浏览器客户端上。（cookie数据存储在浏览器客户端上的。）
- session是将会话的状态保存在服务器端上。（session对象是存储在服务器上。）

在HTTP协议中是这样规定的：当浏览器发送请求的时候，会自动携带该path下的cookie数据给服务器。（URL。）

- 实际上访问以上的这个：index.jsp，底层执行的是：index_jsp.class 这个java程序。
- 这个index.jsp会被tomcat翻译生成index_jsp.java文件，然后tomcat服务器又会将index_jsp.java编译生成index_jsp.class文件
- 访问index.jsp，实际上执行的是index_jsp.class中的方法。
- jsp实际上就是一个servlet  

- jsp的生命周期和Servlet的生命周期完全相同。完全就是一个东西。没有任何区别。
- jsp和servlet一样，都是单例的。（假单例。）

- JSP是：JavaServer Pages的缩写。（基于Java语言实现的服务器端的页面。）
- Servlet是JavaEE的13个子规范之一，那么JSP也是JavaEE的13个子规范之一。

index_jsp 类继承 **HttpJspBase，**而HttpJspBase类继承的是HttpServlet。所以index_jsp类就是一个Servlet类。

JSP既然本质上是一个Servlet，那么JSP和Servlet到底有什么区别呢？

- 职责不同：
  - Servlet的职责是什么：收集数据。（Servlet的强项是逻辑处理，业务处理，然后链接数据库，获取/收集数据。）
  - JSP的职责是什么：展示数据。（JSP的强项是做数据的展示）

什么是javabean？实际上javabean你可以理解为符合某种规范的java类，比如：

- javabean（java的logo是一杯冒着热气的咖啡。javabean被翻译为：咖啡豆）
- 有无参数构造方法
- 属性私有化
- 对外提供公开的set和get方法
- 实现java.io.Serializable接口
- 重写toString
- 重写hashCode+equals

JSP的九大内置对象

- jakarta.servlet.jsp.PageContext pageContext       页面作用域
- jakarta.servlet.http.HttpServletRequest request 请求作用域
- jakarta.servlet.http.HttpSession session  会话作用域
- jakarta.servlet.ServletContext application 应用作用域
  - pageContext < request < session < application
  - 以上四个作用域都有：setAttribute、getAttribute、removeAttribute方法。
  - 以上作用域的使用原则：尽可能使用小的域。

- java.lang.Throwable exception   

- jakarta.servlet.ServletConfig config

- java.lang.Object page  （其实是this，当前的servlet对象）

- jakarta.servlet.jsp.JspWriter out  （负责输出）
- jakarta.servlet.http.HttpServletResponse response （负责响应）

- 目标Servlet是否执行，取决于两个条件：

  - 第一：在过滤器当中是否编写了：chain.doFilter(request, response); 代码。
  - 第二：用户发送的请求路径是否和Servlet的请求路径一致。
- chain.doFilter(request, response); 这行代码的作用：

  - 执行下一个过滤器，如果下面没有过滤器了，执行最终的Servlet。

Filter默认情况下，在服务器启动阶段就实例化。Servlet不会。

Filter过滤器这里有一个设计模式：

- 责任链设计模式。

责任链设计模式最大的核心思想：

- 在程序运行阶段，动态的组合程序的调用顺序。