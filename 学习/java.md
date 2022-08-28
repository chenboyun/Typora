[(32条消息) Java笔试面试题整理第四波_山代王的博客-CSDN博客](https://blog.csdn.net/shakespeare001/article/details/51274685)



ArrayList 

HashMap

HashSet

java并发编程  [黑马程序员全面深入学习Java并发编程，JUC并发编程全套教程_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV16J411h7Rd?spm_id_from=333.337.search-card.all.click&vd_source=14dd36e0ffe11b8a93626170e816f2d7)

JVM底层原理[【狂神说Java】JVM快速入门篇_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1iJ411d7jS?spm_id_from=333.337.search-card.all.click&vd_source=14dd36e0ffe11b8a93626170e816f2d7)

内存结构    垃圾回收算法   类加载机制  



按需加载：需要就加载，不需要就不加载，在jre/lib里面有

![image-20220805082954897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220805082954897.png)

加载子类的时候也会把父类的构造方法执行

类加载器也是一个程序，代码 

jsp会转化成一个java文件，然后编译成.class文件

# 牛客Java练习题

![image-20220812095139288](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220812095139288.png)

1、为了更好地组织类，Java提供了包机制。包是类的容器，用于分隔类名空间。如果没有指定包名，所有的示例都属于一个默认的无名包。Java中的包一般均包含相关的类，java是跨平台的，所以java中的包和操作系统没有任何关系，java的包是用来组织文件的一种虚拟文件系统。A错
2、import语句并没有将对应的java源文件拷贝到此处仅仅是引入，告诉编译器有使用外部文件，编译的时候要去读取这个外部文件。B错
3、Java提供的包机制与IDE没有关系。C错
4、定义在同一个包（package）内的类可以不经过import而直接相互使用。

java.lang.NullPoninterException：变量未被初始化、对象未赋值、对象为空（俗称的空指针异常）
java.lang.NumberFormatException：数据格式转换失败（integer的取值范围为：-128~127，超过范围都会访问false）
java.lang.RuntimeException：运行时异常
java.lang.ArrayindexOutOfBoundsException：数组下标越界

数据类型包括基本数据类型和引用数据类型；基本数据类型：byte,short,int,long,char,float,double,boolean；引用数据类型：数组，接口，枚举，类，空类

main的正确形参   String[] args / String args[] / String... args

**Abstract表示抽象类，抽象类本身不可实例化，必须有子类去继承，且子类中实现抽象父类中所有的抽象方法，子类才可实例化。****final修饰的类，不可继承。****这个修饰符功能相克的。**

抽象类不能实例化

而常量池中的字符串，只有变量名不同是可以用双等号判断是否相等的，内存都是常量池中的字符串。

但是new出来的字符串，只能用equals，用双等号是不相等的，因为是两个内存对象。

{          常量池中的字符串，只有变量名不同是可以用双等号判断是否相等的，内存都是常量池中的字符串。

但是new出来的字符串，只能用equals，用双等号是不相等的，因为是两个内存对象。

"=="和equals()方法的区别和联系
 "=="比较基本数据类型时比较的是表面值内容，而比较两个对象时比较的是两个对象的内存地址值

对于equals方法，注意：**equals方法不能作用于基本数据类型的变量**

如果没有对equals方法进行重写，则比较的是引用类型的变量所指向的对象的地址；

诸如String、Date等类对equals方法进行了重写的话，比较的是所指向的对象的内容
　　　　
简单概括就是：

== 在基本数据类型：值内容, 引用类型时：地址
equals 重写：值内容 ， equals不重写：地址                           }

![img](https://uploadfiles.nowcoder.com/images/20181010/5032673_1539139922699_59B2900AA03CB2182A51CDB520B535B6)

JAVA的JVM的内存可分为3个区：堆(heap)、栈(stack)和方法区(method)7

- 栈区:

1. **每个线程包含一个栈区**，栈中只保存方法中（不包括对象的成员变量）的**基础数据类型和自定义对象的引用(不是对象)**，对象都存放在堆区中。
2. 每个栈中的数据(原始类型和对象引用)都是私有的，其他栈不能访问。
3. 栈分为3个部分：基本类型变量区、执行环境上下文、操作指令区(存放操作指令)。

- 堆区:

1. 存储的全部是对象实例，每个对象都包含一个与之对应的class的信息(class信息存放在方法区)。
2. **jvm只有一个堆区(heap)被所有线程共享**，堆中不存放基本类型和对象引用，只存放对象本身，几乎所有的**对象实例和数组**都在堆中分配。

- 方法区:

1. 又叫静态区，跟堆一样，被所有的线程共享。它用于存储已经被虚拟机加载的类信息、常量、静态变量、即时编译器编译后的代码等数据。

![image-20220812102109448](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220812102109448.png)

引用类型判断时，==判断的是地址是否相等。如果用常量字符串来定义的（如s1，s2，s4）会存在常量池里面；用变量定义的就不会（如s3，s5）。所以上面的状态就是s1==s2；s4==“codercoder”；s3！=s4；s3！=s5。

ANT与maven{

Ant是软件构建工具，Maven的定位是软件项目管理和理解工具。
Ant特点 
没有一个约定的目录结构 必须明确让ant做什么，什么时候做，然后编译，打包 没有生命周期，必须定义目标及其实现的任务序列 没有集成依赖管理
Maven特点
拥有约定，知道你的代码在哪里，放到哪里去 拥有一个生命周期，例如执行 mvn install 就可以自动执行编译，测试，打包等构建过程 只需要定义一个pom.xml,然后把源码放到默认的目录，Maven帮你处理其他事情 拥有依赖管理，仓库管理}

构造函数只能被调用，不能被继承。子类默认调用父类无参构造器，若父类没有无参构造器，子类需要用super()调用父类有参构造器，且super()位于子类构造器的第一行。

因为**接口中方法默认是 abstract public,所以在接口只写函数声明是符合语法规则**。但是**变量默认是用public final static 修饰的，意思它是静态常量，常量不管在接口中还是类中必须在声明时初始化！**所以C的后半句是错的，必须在声明时并给出初始化！**接口中只有常量定义，没有变量声明。**

被static修饰的变量称为静态变量，静态变量属于整个类，而局部变量属于方法，只在该方法内有效，所以static不能修饰局部变量

堆{

-Xmx：最大堆大小

-Xms：初始堆大小

-Xmn:年轻代大小

-XXSurvivorRatio：年轻代中Eden区与Survivor区的大小比值

年轻代5120m， Eden：Survivor=3，Survivor区大小=1024m（Survivor区有两个，即将年轻代分为5份，每个Survivor区占一份），总大小为2048m。

-Xms初始堆大小即最小内存值为10240m

}

编译器根据函数的不同的参数表，对同名函数的名称做修饰，那么对于编译器而言，**这些同名函数就成了不同的函数。**但重写则是子类方法对父类的方法的延申，即子类不仅继承了父类的方法，还向父类的方法中添加了属于自己的内容，改变了父类方法原本的内容，而final代表了一种不可变，这明显与重写形成了冲突。因此被final修饰的类可以被重载但不能被重写，选项C错误。

数据域，也就是个成员变量(类的属性)

局部变量可以和成员变量重名，不加“this”修饰时，优先使用最近的变量。

**instance是java的二元运算符，用来判断他左边的对象是否为右面类（接口，抽象类，父类）的实例**

。自动装箱的时候，java编译器会默认**调用valueOf进行装箱**，**拆箱时会调用**Value方法。**

```
JAVA 子类重写继承的方法时,不可以降低方法的访问权限，子类继承父类的访问修饰符要比父类的更大，也就是更加开放，假如我父类是protected修饰的，其子类只能是protected或者public，绝对不能是friendly(默认的访问范围)或者private
```

File类是对文件整体或者文件属性操作的类，例如创建文件、删除文件、查看文件是否存在等功能，不能操作文件内容；文件内容是用IO流操作的。

构造器本身并没有任何返回值。

![img](https://uploadfiles.nowcoder.com/images/20170823/3252049_1503481716783_5F2B3F671C6B7F8E2385061066EFCE0C)

```
注意throws是写在方法上，申明要抛出的异常。throw是抛出异常。
```

![image-20220812122448506](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220812122448506.png)

（守护线程）daemon线程的终止条件是当前是否存在用户线程,daemon线程创建的子线程任然是daemon线程.

如果文件中没有公共类的话，则文件名和类名不做强制要求

静态方法是使用static关键字修饰的方法，属于类的，不属于对象；非静态方法是不使用static关键字修饰的普通方法，属于对象，不属于类。2、静态方法可以直接调用，类名调用和对象调用；非静态方法只能通过对象调用。

**substring**  方法将返回一个包含从  *start*  到最后（不包含  *end*  ）的子字符串的字符串

接口里面的变量默认都是public static final 的，它们是公共的,静态的,最终的常量.相当于全局常量，可以直接省略修饰符。

实现类可以直接访问接口中的变量

![img](https://uploadfiles.nowcoder.com/images/20200209/5571214_1581249080981_849A4BAB861AC41B9E77D6F856A5E22E)

(构造器、静态初始化块、实例初始化块不继承）

![img](https://uploadfiles.nowcoder.com/images/20170304/837161_1488616442711_250E74268F38A4202D8C30E4329DEBCC)

![img](https://uploadfiles.nowcoder.com/images/20180704/3807435_1530666258064_20577AE82E2EC5D6D44DD2CA01C99BBA)

因为error是系统出错，catch是无法处理的，难以修复的，RuntimeException不需要程序员进行捕获处理，error和exception都是throwable的子类，我们只需要对exception的实例进行捕获即可

带有{}的就是方法体，即使里面是空的

![image-20220812151611863](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220812151611863.png)

![img](https://uploadfiles.nowcoder.com/images/20161218/8207485_1482023299700_17C2F187026D0B45BE3F7CEDF72794A5)

只有当finally块执行完成后，系统才会再次跳回来执行try块、catch块里的return或throw语句；

this的作用其中一个就是在一个构造方法中调用另一个构造方法，

局部内部类{1）局部内部类与局部变量一样，不能使用访问控制修饰符（public、private 和 protected）和 static 修饰符修饰。

2）局部内部类只在当前方法中有效。}

取模运算，结果的符号和被除数符号一致，

String类对equals方法进行了重写，用来比较指向的字符串对象所存储的字符串是否相等。其他的一些类诸如Double，Date，Integer等，都对equals方法进行了重写用来比较指向的对象所存储的内容是否相等

Float类和Double类都重写对于的equals方法，在比较之前都会判断是否同属于Float对象或Double对象，

unicode中一个汉字是可以用一个char表示的

synchronized可以修饰方法、代码块或对象，并不修饰变量。

static修饰的方法只能访问类的成员变量

![img](https://uploadfiles.nowcoder.com/images/20211028/348470426_1635431780619/6479D7BB01736CCC61B8270D41F00B17)

jvm堆分为：新生代（一般是一个Eden区，两个Survivor区），老年代（old区）。常量池属于 PermGen（方法区）

。volatile用于限定变量只能从内存中读取，保证对所有线程而言，值都是一致的。但是volatile不能保证原子性，也就不能保证线程安全。

1.String对象的两种创建方式:
第一种方式: String str1 = "aaa"; 是在常量池中获取对象("aaa" 属于字符串字面量，因此编译时期会在常量池中创建一个字符串对象)，

第二种方式: String str2 = new String("aaa") ; 一共会创建两个字符串对象一个在堆中，一个在常量池中（前提是常量池中还没有 "aaa" 字符串对象）。

```
子类构造方法在调用时必须先调用父类的，由于父类没有无参构造，必须在子类中显式调用，修改子类构造方法如下即可：
public` `Derived(String s){
    ``super``(``"s"``);
    ``System.out.print(``"D"``);
  ``}
```

hashCode()的存在是为了查找的快捷性,用于在散列存储结构中确定对象的存储地址

如果两个对象 equals相等,则 hashCode()也一定相等

如果 equals方法被重写,则 hashCode()也应该被重写

如果两个对象的 hashCode()相等, equals()方法不一定相等

equals方法没有重写,比较的就是应用类型的变量所指向的对象的地址

也可以说 switch语句只支持int类型

整数默认是int类型，int类型不能转型为Double，最多通过自动装箱变为Integer但是Integer与Double没有继承关系，也没法进行转型。

  父类静态代码块 ->子类静态代码块 ->父类非静态代码块 -> 父类构造函数 -> 子类非静态代码块 -> 子类构造函数。

在执行main方法之前，就会加载父类和子类的class文件，并执行其静态语句块

非静态代码块是在类new一个实例的时候执行，而且是每次new对象实例都会执行。
静态代码块服务于类，非静态代码块和构造器都是服务于对象。

相同类型的变量、调用同一个方法时呈现出多种不同的行为特征，这就是多态。

![img](https://uploadfiles.nowcoder.com/images/20171024/9430388_1508834386231_FE8B1A979ADF6E3C2C114AF3F9CA693C)

在java中静态方法中不能使用非静态方法和非静态变量。但非静态方法中可以使用静态变量

**重写是子类对父类的允许访问的方法的实现过程进行重新编写, 返回值和形参都不能改变。** **即外壳不变，核心重写！**（只更改逻辑）

声明一个数组时，不能直接限定数组长度，只有在创建实例化对象时，才能对给定数组长度.。

**真数组：** 数组元素在内存中是一个接着一个线性存放的，通过第一个元素就能访问随后的元素，避免了数据覆盖的可能性，

服务器端：ServerSocket提供的实例 ServerSocket server = new ServerSocket(端口号) 

客户端：Socket提供的实例 Socket client = new Socket(IP地址，端口号)

简单记忆线程安全的集合类： **喂！SHE！  喂是指** **vector，S是指 stack，** **H是指**  **hashtable，E是指：Eenumeration**

![img](https://uploadfiles.nowcoder.com/images/20200805/643412545_1596634989327_DEF638F8839D3C558612E08DC0A11BFF)

不指定ArrayList类型，存入数据，再次取出时，默认是Object类型；但这个题的关键是instanceof关键字，instanceof执行时类似利用java反射机制，识别对象信息。。instance of是根据动态类型判断的

**static块和方法不能出现this和super....可以的，实例对象也可以调用静态方法。**this表示当前类的对象，由static修饰的方法是由类直接调用，不需要创建对象，所以在static里不能用this.

![img](https://uploadfiles.nowcoder.com/images/20160727/6316247_1469628859864_A8BB53E66CC9A072C0448DDDBDF4C3B2)

局部内部类就像是方法里面的一个局部变量一样，是不能有public、protected、private以及static修饰符的。

一个类实现接口，要实现该接口的所有抽象方法。

接口不能被实例化，但可以声明，但是必须引用一个实现该接口的对象。

从设计层面来说，抽象类是对类的抽象，是一种模板设计，接口是行为的抽象，是一种行为的规范。

boolean类型不能和任何类型进行转换，会报出类型异常错误。

循环过程中list.size()的大小变化了，就导致了错误。
所以，如果你想在循环语句中删除集合中的某个元素，就要用迭代器iterator的remove()方法，因为它的remove()方法不仅会删除元素，还会维护一个标志，用来记录目前是不是可删除状态，

ntValue()是把Integer对象类型变成int的基础数据类型；
parseInt()是把String 变成int的基础数据类型；
Valueof()是把String 转化成Integer对象类型；

1、运行时异常不需要程序员去处理，当异常出现时，JVM会帮助处理。常见的运行时异常有：

ClassCastException(类转换异常)

ClassNotFoundException

IndexOutOfBoundsException(数组越界异常)

NullPointerException(空指针异常)

ArrayStoreException(数组存储异常，即数组存储类型不一致)

还有IO操作的BufferOverflowException异常

2、非运行异常需要程序员手动去捕获或者抛出异常进行显示的处理，因为Java认为Checked异常都是可以被修复的异常。常见的异常有：

IOException

SqlException

forward，服务器获取跳转页面内容传给用户，用户地址栏不变

redirect，是服务器向用户发送转向的地址，redirect后地址栏变成新的地址

floor ： 意为地板，指向下取整，返回不大于它的最大整数 ceil ： 意为天花板，指向上取整，返回不小于它的最小整数 round ： 意为大约，表示“四舍五入”，而四舍五入是往大数方向入。

null表示没有地址；null可以赋值给引用变量，不能将null赋给基本类型变量，

static 静态成员属性不能使用 this 关键字调用

![img](https://uploadfiles.nowcoder.com/images/20190724/807493545_1563932229873_C30CDF07DDFF9A43D6E37E2A6E74D4E4)

1. 把线程的run方法当普通方法，就直接用实例.run()执行就好了。没有看到start。所以是普通方法调用。

数值型变量在默认情况下为Int型，byte和short型在计算时会自动转换为int型计算，结果也是int 型。

synchrozied关键字称作同步，主要用来给方法、代码块加锁，被加锁的代码段，同一时间内多线程同时访问同一对象的加锁方法/代码块时，只能有一个线程执行能执行方法/代码块中的代码，其余线程必须等待当前线程执行完以后才执行该方法/代码块。

volatile关键字1.保证了不同线程对该变量操作的内存可见性.(当一个线程修改了变量,其他使用次变量的线程可以立即知道这一修改)。2.禁止了指令重排序.

Lock接口提供了与synchronized关键字类似的同步功能，但需要在使用时手动获取锁和释放锁。

transient关键字 简单地说，就是让某些被修饰的成员属性变量不被序列化。

调用Base这个构造方法应该这样 new Base(a,b)

方法区是什么？
方法区是广义上的概念，是一个定义、标准，可以理解为Java中的接口，在Jdk6、7方法区的实现叫永久代；Jdk8之后方法区的实现叫元空间，并从JVM内存中移除，放到了直接内存中；
方法区是被所有方法线程共享的一块内存区域.

运行时常量池是什么？
运行时常量池是每一个类或接口的常量池的运行时表示形式.

具体体现就是在Java编译后生成的.class文件中，会有class常量池，也就是静态的运行时常量池；



运行时常量池存放的位置？

运行时常量池一直是方法区的一部分，在不同版本的JDK中，由于方法区位置的变化，运行时常量池所处的位置也不一样.JDK1.7及之前方法区位于永久代.由于一些原因在JDK1.8之后彻底祛除了永久代,用元空间代替。


运行时常量池存放什么？
存放编译期生成的各种字面量和符号引用；（字面量和符号引用不懂的同学请自行查阅）
运行时常量池中包含多种不同的常量，包括编译期就已经明确的数值字面量，也包括到运行期解析后才能够获得的方法或者字段引用。 此时不再是常量池中的符号地址了，这里换为真实地址。

运行时常量池与字符串常量池？（可能有同学把他俩搞混）
字符串常量池：在JVM中，为了减少相同的字符串的重复创建，为了达到节省内存的目的。会单独开辟一块内存，用于保存字符串常量，这个内存区域被叫做字符串常量池.

字符串常量池位置？

JDK1.6时字符串常量池，被存放在方法区中（永久代），而到了JDK1.7，因为永久代垃圾回收频率低；而字符串使用频率比较高，不能及时回收字符串，会导致导致永久代内存不足，就被移动到了堆内存中。

字面量(literal)是用于表达源代码中一个固定值的表示法(notation). int i = 1;把整数1赋值给int型变量i，整数1就是Java字面量， String s = "abc";中的abc也是字面量。

修饰非静态方法 锁的是this 对象

修饰静态方法 锁的是class对象

被fianl修饰的变量不会自动改变类型，当2个final修饰相操作时，结果会根据左边变量的类型而转化。

包装类的“==”运算在不遇到算术运算的情况下不会自动拆箱

包装类的equals()方法不处理数据转型

abstract类不能用来创建abstract类的对象；

线程安全问题都是由全局变量及静态变量引起的。
若每个线程中对全局变量、静态变量只有读操作，而无写操作，一般来说，这个全局变量是线程安全的；若有多个线程同时执行写操作，一般都需要考虑线程同步，否则就可能影响线程安全。

旦垃圾回收器准备好释放对象占用的存储空间，将首先调用其finalize()方法， 并且在**下一次**垃圾回收动作发生时，才会**真正的**回收对象占用的内存

即使Test test=null;这里也会加载静态方法，所以test数据中包含Test类的初始化数据。（静态的，构造的，成员属性）

count = count++ 原理是 temp = count； count = count+1 ； count = temp；  因此count始终是0 

 子类的构造方法总是先调用父类的构造方法，如果子类的构造方法没有明显地指明使用父类的哪个构造方法，子类就调用父类不带参数的构造方法。
而父类没有无参的构造函数，所以子类需要在自己的构造函数中显示的调用父类的构造函数。

final类型的变量一定要初始化，因为final的变量不可更改。

