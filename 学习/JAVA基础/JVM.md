[NOTE_JVM: 尚硅谷JVM全套教程，百万播放，全网巅峰（宋红康详解java虚拟机）学习笔记 - Gitee.com](https://gitee.com/vectorx/NOTE_JVM/tree/main)



[深入理解java虚拟机读后总结 - 王菜鸟1993 - 博客园 (cnblogs.com)](https://www.cnblogs.com/JamesWang1993/p/8548763.html)

[(32条消息) 《深入理解Java虚拟机》读书笔记--面试全面复习_ZhiZDK的博客-CSDN博客](https://blog.csdn.net/qq_43713797/article/details/123461772)

openJDK和OracleJDK所遵守的协议不一样

视频看 p01-p203  ，p266-p301就可以啦

有一个别人开发的GC  OracleJDK里面没有    商用的居然比免费的少

人工智能自己计算了一些东西出来而我们不了解会不会出现一些灾难性的问题

**android虚拟机分为Dalvik虚拟机和ART虚拟机。**是Google公司设计的用于android平台的虚拟机，google参考Java虚拟机，根据移动设备的一些特性进行优化，最终形成了android的虚拟机。android虚拟机是面向Linux，嵌入式操作系统的虚拟机（适配硬件与指令集）1、android虚拟机CPU指令基于寄存器的，而JVM基于栈。基于寄存器的虚拟机对于编译后变大的程序来说，在它们执行的时候，花费的时间更短。2、android虚拟机执行文件为.dex，而JVM运行java字节码。

JIT 二次编译

栈架构是8位对齐而寄存器架构（如Android）是16位对齐的，指令集更大	

运行时数据区：

KVM：更加轻量化，，低端市场可以用，比如传感器和老人机

看大公司用什么技术，你自己去用肯定错不了

淘宝JVM实现了不同虚拟机之间的数据共享

和硬件以及系统耦合深的，性能都会比较好

生成的常量池加载到内存里就叫做运行时常量池

![image-20221101180030365](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221101180030365.png)

<clinit>就是为了把静态的变量赋值，没有静态变量就没他

![image-20221101184126944](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221101184126944.png)

因为做虚拟机的时候C  C++大行其道  所有本地方法栈什么的

虚拟机就是一个进程

JIT编译产物周志明老师把他放进去了，阿里拿出来了，不用考虑太多，知道是独立于堆就行

PC寄存器存储的是字节码指令地址

![image-20221102162024802](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221102162024802.png)那么普通的static函数没有this  就不能使用this.????这个语法了

一般都是用int存储的，比如int a = 8;![image-20221102182853214](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221102182853214.png)

![image-20221102184409701](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221102184409701.png)

运行时常量池是字节码文件中的常量池，跑起来的时候在方法区中

要从符号引用变成直接引用，之后找到需要的方法之类的

晚期绑定或动态链接绑定，比如传进接口类或者父类![image-20221102191136007](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221102191136007.png)

全是非虚的![image-20221102194857824](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221102194857824.png)

直接调用父类的final方法会是invokeverial   但是她其实是非虚方法，显式的调用就是super.finalmethoed    -->  invokespecial

有了虚方法表就不用一层一层往上判断了

![image-20221103175147470](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221103175147470.png)堆的组成![image-20221103175236845](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221103175236845.png)



线上环境通常设置初始内存和最大内存一致，免得频繁增加和释放影响性能（GC）

加号是不关闭![image-20221103182422215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221103182422215.png)并不是8：1:1  而是6 ： 1： 1   想*8： 1 ： 1  需要自己指定![image-20221103182805319](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221103182805319.png)

from   区  和  to  区    循环的一个名字

什么时候会触发minorGC?  eden 满了的时候   但是幸存者区满了不触发（但是他也有垃圾回收）（eden 满了的时候回吧他和from 区一起进行回收）

major  GC   full GC有点像  前期混着用的	

后两个GC时间会长十倍以上

字符串之前是放在方法区，后来放在元空间

内存分配自适应会出现s1  !=  s2![image-20221104140102980](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104140102980.png)

动态年龄判断：翻来覆去挺耗时的，所以就一起放到老年代了

如果  S1  S2  很小，直接就扔进老年代了一样，那么yong GC就没有什么意义了；；如果ENEN小的话频繁yongGC 会挤占用户线程资源

字节码文件加载到内存之后才有去掉锁的操作，字节码文件里面仍旧有锁

虽然有栈上分配，但是并没有被应用，倒是标量替换是有的，所以对象都是分配在栈上的

方法区里面的东西很多都不是new 出来的，比如class  或者一些方法<init>

![image-20221104162927794](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104162927794.png)可以看做方法区是一个接口而永久代之类的是一个实现

![image-20221104183834548](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104183834548.png)扔到方法区之后Class文件会记录他的类加载器。而类加载器也会记录它加载了哪些类；一开始的文件是没有的

构造器是一种方法：<init>



操作数栈最大深度；局部变量表数组长度；参数大小![image-20221104184340107](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104184340107.png)（有一个this所以是2)

![image-20221104190806501](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104190806501.png)没有实例也能访问static

![image-20221104190850530](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104190850530.png)用final修饰了的静态常量

![image-20221104191351371](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221104191351371.png)最后一行可以看到加了final的static在编译的时候就有值了

ipush  iload  是在操作数栈里面取数字加数字的操作；；istore是在本地变量表的操作

有了收购JRockit 的想法，之后把永久带从HotSpot里面移出去了；官方当时说将JRockit融合了，而他的用户没有永久带，所以就给取消了；调优困难（fullGC,） 分配dda大小困难

在8中静态变量和字符串常量还是放在堆之中的1.6是放在永久带上的

![image-20221105150213280](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221105150213280.png)

不是所有对象都有自己的.class指针

直接指针：句柄访问：稳定，对象移动但是句柄池改位置，但是栈空间没有变化   直接指针：节省空间，访问快速

64位操作系统（JDK）默认是C2   server

C2编辑器是C++编写的

![image-20221105201720897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221105201720897.png)

.class文件变成了  .so  ![image-20221105202119814](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221105202119814.png)

1.8s是char[]数组之后一点九往后就是![image-20221106125148665](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106125148665.png)

堆里面字符串太多了而存储的很多都是拉丁文，一个byte就能存储，；所以使用了byte数组并且加了一个编码标识（看看是不是中文之类的）

总的来说就是，JDK1.7之前，运行时常量池（字符串常量池也在里边）是存放在方法区，此时方法区的实现是永久带。
JDK1.7字符串常量池被单独从方法区移到堆中，运行时常量池剩下的还在永久带（方法区）
JDK1.8，永久带更名为元空间（方法区的新的实现），但字符串常量池池还在堆中，运行时常量池在元空间（方法区）。（疯狂放字符串，最后发现是堆溢出了![image-20221106141221428](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106141221428.png)

)运行时常量池很重要，所以应该放在方法区

string的不可变性就是他想用就要自己造一个，别用别人的

跑一个程序一上来就两千多个，1009显然不够

编译器的优化![image-20221106144539899](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106144539899.png)常量与常量的拼接会在常量池里

只要有一个是变量，就先放到堆里面![image-20221106145125010](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106145125010.png)会去new 一个string builder  ![image-20221106145644269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106145644269.png)![image-20221106145815169](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106145815169.png)

![image-20221106145903272](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106145903272.png)但是有一点区别

上面的可以知道一个在常量池里一个在堆里，地址不一样

不是变量，是常量的方式，所以是相同的![image-20221106150219761](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106150219761.png)

编译阶段  final就确定了   准备阶段有一个静态变量的初始化

![image-20221106153345585](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106153345585.png)

![image-20221106153937093](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106153937093.png)

没有在常量池中生成A B ![image-20221106154335323](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106154335323.png)

![image-20221106154553049](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106154553049.png)

str.intern 后面没有接着的，这行代码就没有意义，因为他返回的是常量池中的对象，不会更改str

做实验的时候要用一些偏门的字符串，否则他可能已经在里面了 

在7以后为了省内存，他不会再在方法区中弄一个了，方法区中记录的就是new出来的地址![image-20221106163754973](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221106163754973.png)就是常量池中记录了堆中new出来的地址  

s3.intern()   s3->s3    之后他生成的字符串常量池里面的内容指向s3   所以s4->常量池->s3

string str =  new string()+ new string()   在常量池里面并没有他

intern出来的如果命中了，堆里的对象可以回收

JDK有什么变化；为什么会有这些变化，未来还会有什么变化

![image-20221107131617113](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221107131617113.png)

GC root ：回收区域之外的都可以临时作为GCroot，比如老年代中引用了新生代的对象![image-20221107132940501](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221107132940501.png)

ffinalized  执行优先级很低，而且只有在GC时才执行

GCroot   上千个，尽管我只放了几行代码

标记清楚算法标记的是可达的 根节点的对象；第一次遍历只看根节点相关，第二次要把堆都遍历一遍；清除并不是真的清除![image-20221107161007357](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221107161007357.png)

如上可知；硬盘格式化之后没有往里面写入数据，都是可以恢复的

复制算法希望大部分数据都得死，这样能少复制；server的特点（对象朝生夕死）就很契合

标记整理在老年代不合适，所以之后又发明了标记压缩；对于老年代多一个空白空间太奢侈了；他会记录自己的边界

前三种算法是基础，分代收集算法是具体问题具体分析，对不同的代是不同的

软引用弱引用可以用来做手机内存

![image-20221107193828071](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221107193828071.png)

内存泄露就是公摊，内存溢出就像是屋子里没地方了

忘记断开引用可能导致内存泄露 ；JAVA没有使用引用计数算法，所以不会产生相关的内存泄露；单例；忘记close

三级缓存   内存  本地  网络

weakHashMap<>    ![image-20221108151206153](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108151206153.png)使用了自己的entry，继承自弱引用

准备回收对象的时候如果他有虚引用，那么可以把它放进虚引用队列，此时队列非空，可以做一些操作![image-20221108152848785](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108152848785.png)

还有一个终结器引用![image-20221108153019848](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108153019848.png)

目前追求的是STW![image-20221108172628746](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108172628746.png)暂停时间和内存是 矛盾的

CMS   应该算是第一款真真意义上的并发回收器，但是2020年JDK4给他删除了

![image-20221108174805768](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108174805768.png)JDK9彻底移除了红线

CMS  和Parallel  不是一个GC框架，所以不能一起用

pernew失宠了，没有搭档，单线程用serial  多线程用parallel![image-20221108184054568](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221108184054568.png)

CMS后备方案是一个单线程的，而现在都是多核CPU，相对而言他的性能太差了

啊 full  GC之后有一个参数可以开启一个压缩算法；同时切换到signal之后

有不同代的收集器是因为他们使用的算法不同，适用于不同的场景

有并行执行就肯定会有STW；G1是兼具并行与并发的，并行吞吐量会大一些

大对象在G1需要连续的区域

回收的时候GC ROOT 的概念可能被放大，比如在老年region和yongregion相互持有引用

记忆集：每个region都有，记录我是谁的引用，就不需要遍历了；每次写引用的时候都会看看是不是在其他region，那样的话可能会修改卡表

写屏障![image-20221109151746076](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221109151746076.png)

只有eden满了会主动出发yungGC  而server只会被动触发GC

JDK7大对象把之前的同期放进老年区；JDK8大对象直接进入老年区（在新生代满了的时候）

官方并没有强制要求使用   javac

![image-20221110133208683](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221110133208683.png)

只有常量池计数器有   从1  开始，比如计数器说是22哥其实只有21个

加载到内存不使用全限定名而是用简单名称，说明加载到内存了，就是直接引用而不是字符引用了

final常量   字节码文件里面就已经赋值了

字节码表结构里面没有写继承自父类或者接口的变量

![image-20221110183006652](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221110183006652.png)只能说规范里字节码是允许重名的，虚拟机本身不包括字节码结构的，他是从类加载器加载开始的

int是四个字节   byte  short转化为有符号的，boolean转化为无符号的

操作码一字节，操作数两个字节

需要两个槽位![image-20221112141326524](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112141326524.png)

压入-1是  iconst_m1

double a = 3/0.0  结果是Infinity   溢出了，是无穷大，如果是int    那么就会是错误，如果0.0/0.0   是不确定的值NaN

局部变量表并不是一开始就是满的，是在CODE不断的运行中，有一部分是istore进去的

i+=10   用的字节码是linc  位置  by   10

取反的机器码是取一个-1（iconst_m1）入栈，然后他们进行异或

没有别的运算   ++i  和  i++   是一样的，字节码是一样的

isotre_1   取出栈顶，放在局部变量表1 d

![image-20221112162123642](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112162123642.png)入栈i  加载进去 i 到局部变量表；取出i;对局部变量表的1自增，与栈没有关系，放回去；放到位置2；

（这个应该只是比较宽泛的标准，最终还是需要生成对应的机器码才能执行。最终的机器码如何，不得而知！上有标准、下有硬件，中间随你发挥；标准是标准实现是实现）

![image-20221112163312895](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112163312895.png)

自增大部分实现都是与栈，原地自增，但是之前取出了他的值，在之后他自增，然后又放回来赋值了，是由于自增和赋值的数是同一个位置的原因

在类型转化时，槽位数量可能有变化

int 4字节，long8字节，转化为float可能会有精度损失，因为无法兼顾空间占用小和精度；long转化为double也可能出事

char  byte short  被当做int  甚至类型转化的时候都被当做int;全是i2d   i2f

![image-20221112172516824](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112172516824.png)

局部变量表单位是4个字节

窄化类型转换也叫强制类型转换

long类型转化为int类型   使用了两次类型转化    l2i   i2b;但是short->btey是当成Int   只有  i2b

new  后面加的是个  类的描述![image-20221112184101717](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112184101717.png)

多维数组或是其他数组要把数量传进去![image-20221112185030571](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112185030571.png)

但是new int[10]  []只入一个就可以了，他使用的是![image-20221112185141523](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112185141523.png)相当于是一个一维数组

![image-20221112185438637](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112185438637.png)

如果是printl.out   就是  getstatic System.out   是system里面的静态字段out压入栈  

new对象之后栈里面有一个实体，指向堆内的空间![image-20221112185955258](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112185955258.png)![image-20221112190014289](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112190014289.png)4可以使3复制的一个出栈

get是压栈put是出栈

数组的store  是修改堆内容，而不是栈的

不存在方法的重写![image-20221112193939936](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221112193939936.png)

float aa {int a =1;return a;}有一个隐形的类型转换

很多操作的参数是栈里面的，没重新加载会出现问题

boolean  是用   ireturn 返回的

# 类的加载

在方法区生成一个类的模板，然后堆里面是一个大的Class的实例指向方法区

![image-20221113114904996](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113114904996.png)![image-20221113114913904](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113114913904.png)

![image-20221113115436736](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113115436736.png)

![image-20221113115840223](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113115840223.png)但是我们仍将他归到检验当中

此时做这些事情的时候已经在方法区有类模板对象了![image-20221113121209260](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113121209260.png)

解析度时候才会去执行![image-20221113121731762](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113121731762.png)

验证都通过了，就会有静态属性的赋值问题

加载的时候虽然已经加载了非静态的的，但是并没有赋值

准备阶段给静态变量赋值，不是常量![image-20221113131025767](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113131025767.png)

编译结束就已经对全局常量的值进行了保存，在![image-20221113131214046](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113131214046.png)constantvalue中 ，在常量池中能找到他的值

![image-20221113132701397](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113132701397.png)final  static str = "aaaa";如果是new 的话就没有constantvalue

符号引用转化为直接引用，就是比如说我们需要了解一个object类，但是我们只知道他的符号（全限定名），我们需要知道这个类在哪；就相当于地点和开启了导航；菜谱与去厨房真正的找到工具和食材去做饭

解析环节通常是  初始化之后执行

![image-20221113141224442](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113141224442.png)之前执行的代码都是自己生成的

<clinit>是代码块，是我们自己编写的，只有显式赋值和static![image-20221113142208421](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113142208421.png)

这两个在初始化阶段进行赋值![image-20221113142514016](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113142514016.png)（因为不是基本数据类型)

没有final  肯定是初始化时进行赋值

![image-20221113143034649](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113143034649.png)这种需要调用具体的方法，在准备阶段不可以，所以这个是需要在<clinit>里面实例化一个Random才可以；     重点是，是否用常量进行了显式赋值

![image-20221113143327931](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113143327931.png)![image-20221113143449515](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113143449515.png)

他并没有显式的调用sycnized,所以很难发现，因为我没有在字节码的描述上看到clinit上面有那个标识![image-20221113143938626](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113143938626.png)

同时加载两个类，如果他们A  和  B  A需要加载一个（有一个调用Class.forname(B）)B而B需要加载一个A就会死锁；就是交叉加载可能出现死锁问题

对类 的主动使用会执行，初始化阶段

看过程可以看出来，因为父类先初始化，虽然子类已经加载了，但是他并不需要调用初始化的代码，所以他不初始化

类的主动使用：![image-20221113145518460](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113145518460.png)在代码块中，<clinit>需要执行输出，所以要执行<clinit

>

反序列化也会主动调用

和子类初始化要初始化父类不一样![image-20221113151854643](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113151854643.png)

![image-20221113153235091](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113153235091.png)

数组类的父类也是Object  int[] a;    a.getclass().getsuperclass  打印的是Object,只是定义的话，并不需要初始化（初始化数组元素的类）

![image-20221113155923979](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113155923979.png)

![image-20221113160602240](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113160602240.png)

填充一个  0   的话，就是false![image-20221113161227583](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113161227583.png)

![image-20221113161903321](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113161903321.png)![image-20221113162456645](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113162456645.png)

equals  比较慢，如果想比较两个字符串是否相等，可以先进行==  如果相等再equals

while(i<100){string str = "sss"i++}的字节码![image-20221113163642941](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113163642941.png)就是条件循环和goto的搭配罢了，没有while的结构

for(int i = 0;i<100;i+=){}![image-20221113164025393](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113164025393.png)

可能只有作用域不一样吧![image-20221113164327486](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113164327486.png)

抛出异常  是   athrow   操作数栈会先new 一个异常，然后抛出

throws会多一个   ![image-20221113175247998](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113175247998.png)结构![image-20221113175310141](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113175310141.png)

throws是刻画方法的，不是方法内的，他的结构和CODE是同一级的，而a throw是在方法体里面的![image-20221113175446094](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113175446094.png)

系统已经定义好的运行时异常，字节码是不显示的，会自动的抛出

![image-20221113175702032](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113175702032.png)

异常表记录的是  在字节码中哪些范围会触发哪些异常，然后根据这些异常知道应该跳转到哪；在字节码中并没有try  catch的结构，而是使用异常表![image-20221113180559793](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113180559793.png)

![image-20221113182758151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113182758151.png)蓝色的是异常要执行的，他紧接着monitorexit，这块代码快里面有exit和  a throw，所以不用担心出现异常未解锁；当然蓝色的也可能出现异常，那么重新跑一遍蓝色的就好了

有了class文件和方法区中的数据结构，类加载器就完成任务了

类加载器并没有绑定在JVM的内部，可以有自己独特的加密解密，防止别人偷看

父类加载了，他自己就不能加载了![image-20221113195355256](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113195355256.png)

这是两个类加载器![image-20221113195755852](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113195755852.png)

![image-20221113200126634](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221113200126634.png)

扩展类加载器和系统类加载器由引导类加载器加载

![image-20221114131336186](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114131336186.png)虽然他们都继承自URLClassLoader

下面的类型是[L String     类加载器是引导类加载器![image-20221114132245775](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114132245775.png)

基本数据类型没有类加载器

loadclass(name,resolve)//里面第二个参数决定加载的时候是否解析

类加载器也是通过双亲委派机制加载的（Java代码）???![image-20221114144223085](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114144223085.png)

引导类加载器会check一下判别是否应该有自己加载，否则返回null

双亲委派在  loadclass中实现

![image-20221114144804215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114144804215.png)在URLClassLoader中重写了findClass,下面的用的都是他的；更上面的是空的

findclass会调用Defineclass   这个根据二进制的文件返回实例；返回值就是大的Class实例![image-20221114145055541](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114145055541.png)![image-20221114145118763](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114145118763.png)

![image-20221114145610360](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114145610360.png)

![image-20221114145754512](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114145754512.png)主动使用；被动使用

双亲委派机制可以保证类只有一个类加载器加载了（他有自己的命名空间）；并且可以只由他加载；什么类应该由什么加载器去加载，是确定的；保护安全，防止核心API被篡改（如禁止构建包名  java.lang    防止误导加载器加载错误代码，如果没有双亲委派，可能就加载了）

上下文加载器默认属于      系统类加载器

SPI:核心类库的可接入的接口

最后一棒代码：线程上下文类加载器就是  系统类加载器![image-20221114152857801](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114152857801.png)

高层解决不了，委托上下文类加载器调用具体想调用的类加载器；像一个中介

第三种破坏是一种创新，是不满足树状模型：热部署（我们可以写一个循环，不停的加载字节码文件就好了，之后替换字节码文件就行了）

系统或者扩展类加载器都是在Launcher内部定义的（JDK8）9之后有很大变化![image-20221114161345650](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221114161345650.png)

JDK9中的模块化：先判定是哪个模块负责的，之后没有的话再找父类加载器

Java执行的比如jcmd.exe其实是在lib目录下的jar包中的.class文件中

JDK14起，已不再集成visualvm，需要自己去visualvm官网下载。

生命周期长的引用短的，一直不释放属于内存泄露

![image-20221115173557000](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221115173557000.png)

![image-20221115181248772](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20221115181248772.png)

