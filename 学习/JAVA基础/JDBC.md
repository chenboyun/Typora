### 快捷技巧



反射中 Class.forname("com.mysql.Driver")   会导致类的加载。，用这个来注册驱动；加载类会让静态代码块执行。就直接，会进行驱动的注册

### JAVA中**ResourceBundle**使用

properties文件

方法：

- getObject(String key);
- getString(String key);
- getStringArray(String key);

ResourceBundle bundle = ResourceBundle.getBundle("res", new Locale("zh", "CN"));
String cancel = bundle.getString("cancelKey");
其中new Locale(“zh”, “CN”)提供本地化信息，上面这行代码，程序会首先在classpath下寻找my_zh_CN.properties文件，若my_zh_CN.properties文件不存在，则取找my_zh.properties，如还是不存在，继续寻找my.properties,若都找不到就抛出异常。

### 标准格式

```java
Connection conn = null;
Statement stmt = null;
ResultSet rs = null;//结果集
try{
  Class.forName("com.mysql.jdbc.Driver");
  conn = DriverManager.getConnection("jdbc:mysql://l....");
  stmt = conn.createStatement();
  String sql = "select empno,ename,sal from emp";
  rs = stmt.executeQuery(sql);
  rs.next()//光标下移，返回boolean
}
```

![image-20220514230638853](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220514230638853.png)

![image-20220514230819613](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220514230819613.png)

![image-20220514231016409](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220514231016409.png)

加载类\“com.mysql.jdbc.Driver”。这是弃用。新的驱动程序类是’ **com.mysql.cj.jdbc.Driver**。驱动程序是通过SPI自动注册的，手动加载驱动程序类通常是不必要的。



数据查询语言**DQL**，数据操纵语言**DML**，数据定义语言**DDL**，数据控制语言**DCL**。

想要用户输入不参与编译，就使用statement接口的子类 preparedstatement---预编译的数据库操作对象（先编译，只编译一次，效率更高）

代码变为了

```java
Class.forName("com.mysql.cj.jdbc.Driver");
conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/user","root","123456");
String sql = "select * from user_loin where loginName = ? and loginPwd = ?";//框架，占位符
ps = conn.prepareStatement(sql);//编译
ps.setString(1,loginName);
ps.setString(2,loginPwd);
rs = ps.executeQuery();
```
