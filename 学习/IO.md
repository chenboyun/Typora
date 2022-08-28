[(32条消息) 韩顺平老师-IO流_此生辽阔的博客-CSDN博客_韩顺平java](https://blog.csdn.net/ningmengshuxiawo/article/details/119102854)

##### 创建文件

```java
String path = "e:/data/data";
        File file = new File(path);//仅仅在内存里面
        try {
            file.createNewFile();//底层真正的把对象创建到内存。
        } catch (IOException e) {
            e.printStackTrace();
        }

        File parentFile =new File("e:/");
        String filename = "aaa.txt";
        File file1 = new File(parentFile,filename);
        try {
            file1.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
        
        String parentfile ="e:/";
        String filename2 = "aaa.txt";
        File file3 = new File(parentfile,filename);
        try {
            file1.createNewFile();
        } catch (IOException e) {
            e.printStackTrace();
        }
				file.getName();
        file.getAbsolutePath();//绝对路径
        file.getParentFile();//父目录
        file.length();//几个字节
        file.exists();//是否存在
//  mkdir  创建一个一级目录  mkdirs 创建一个多级目录    delete 删除一个文件或空目录
file.delete   //目录也被当成一种文件存在
  file = new File("e:/aa/bb/cc");
        file.mkdirs();
```

##### 流的分类

子节流    8bit （二进制文件，如照片视频）   字符流 按编码（文本文件）

![image-20220824160542215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220824160542215.png)

##### inputstream

分为;FileInputStream文件输入流     BufferInputStream缓冲字节输入流     ObjectInputStream对象字节输入流

fileinputstream（） 读取，每次读取一个字节readData = fileinputStream.read()    读到末尾返回-1，读取汉字会发生问题因为汉字是3个char

可以一下读取多个字节，  

```java
int readlen = 0;
byte[] b = new byte[8];
FileInputStream fileInputStream = new FileInputStream("e:/ss/a.txt");
readlen = fileInputStream.read(b);
System.out.println(new String(b,0,readlen));
//为了使用fileoutputstream  可以将字符串转化成字符数组
String str = "ssss";
outputstream.write(str.getBytes());  //加一个参数  true 表示append 表示追加
```

filereader使用后必须进行刷新或关闭才能将内容写入，

节点流直接操纵数据源，比较底层，没有包装，处理流对节点流进行了包装，就是装饰者模式，比如buffereader在源码里有一个reader

关闭流的关闭最外层的就可以了因为真正的读取发生在内层，而外层的关闭会调用内层的关闭

buffereader.readline() 读完返回null   

```java
String line = null
line = buffereader.readline();
String path = "e:/ss/ss";
BufferedWriter  bufferedWriter = new BufferWriter(new fileReader(path));
bufferedWriter.write();
bufferedWriter.newLine();
```

string line

不要使用  reader 或 writer读取二进制文件，否则可能造成二进制文件的损坏

bufferedinputstream (继承自 filterInputStream) 与bufferedoutputstream

![image-20220825082223888](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220825082223888.png)

序列化必须实现两个接口中的一个  serializable externalizable

IO很多修饰器，把高一层的装到底层里面基本上都可以

```java
ObjectInputStream  ois = new ObjectInputStream(new FileInputStream()) 	
ObjectOutputStream  oos = new ObjectOutputStream(new FileOutputStream())
oos.writeInt  oos.writeBoolean
ois.readInt//要按照存放的顺序读取//object读取了之后要向下转型
  //out是序列化，in是反序列化
```



![image-20220825090955862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220825090955862.png)

```
private static final long SerialVersionUID= 1L//如果修改了类但是版本号没有变，就会认为他是这个类的升级版，而不是新的类
```

如果一个用户有一些敏感信息（如密码，银行卡号等），为了安全起见，不希望在网络操作（主要涉及到序列化操作，本地序列化缓存也适用）中被传输，这些信息对应的变量就可以加上transient关键字。换句话说，这个字段的生命周期仅存于调用者的内存中而不会写到磁盘里持久化。总之，java 的transient关键字为我们提供了便利，你只需要实现Serilizable接口，将不需要序列化的属性前添加关键字transient，序列化对象的时候，这个属性就不会序列化到指定的目的地中。

标准输入标准输出   sysytem.in   system.out(printStream)

我们可以读取一个子节流指定编码方式转化成字符流，可以解决乱码问题

![image-20220825093509056](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220825093509056.png)

```java
String path = "e:/aa/aa/aa";
InputStreamReader isr= new InputStreamReader(new FileInputStream(path),"gbk");
BufferedReader = new BufferedReader(isr);
```

我们可以根据自己的需要改变printwriter或printreader

```java
PrintWriter pw = new PrintWriter(new FileWriter("e:/eee/ee"));
```

properties

![image-20220825101719151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220825101719151.png)

```
properties properties = new properties();
properties.load(new fileReader("e:/ee/ee"));
String name = properties.getPorperty("name");
properties.setPorterty("name","Tom");
properties.store(new  FileOutputStream("src/aa/aa.properties"))
properties的父类就是hashtable,底层也是他
```

