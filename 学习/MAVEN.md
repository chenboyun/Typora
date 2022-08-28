http://heavy_code_industry.gitee.io/code_heavy_industry/ 

alt+insert  快速实现方法

**mvn archetype:generate**

![images](http://heavy_code_industry.gitee.io/code_heavy_industry/assets/img/img008.be45c9ad.png)

运行 Maven 中和构建操作相关的命令时，必须进入到 pom.xml 所在的目录。如果没有在 pom.xml 所在的目录运行 Maven 的构建命令，那么会看到下面的错误信息：

```java
The goal you specified requires a project to execute but there is no POM in this directory
```

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse03.html#_2、清理操作)2、清理操作

mvn clean

效果：删除 target 目录

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse03.html#_3、编译操作)3、编译操作

主程序编译：mvn compile

测试程序编译：mvn test-compile

主体程序编译结果存放的目录：target/classes

测试程序编译结果存放的目录：target/test-classes

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse03.html#_4、测试操作)4、测试操作

mvn test

测试的报告存放的目录：target/surefire-reports

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse03.html#_5、打包操作)5、打包操作

mvn package

打包的结果——jar 包，存放的目录：target

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse03.html#_6、安装操作)6、安装操作

mvn install

```log
[INFO] Installing D:\maven-workspace\space201026\pro01-maven-java\target\pro01-maven-java-1.0-SNAPSHOT.jar to D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.jar
[INFO] Installing D:\maven-workspace\space201026\pro01-maven-java\pom.xml to D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.pom
```

安装的效果是将本地构建过程中生成的 jar 包存入 Maven 本地仓库。这个 jar 包在 Maven 仓库中的路径是根据它的坐标生成的。

 1Class.forName("com.mysql.cj.jdbc.Driver");2conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/user","root","123456");3String sql = "select * from user_loin where loginName = ? and loginPwd = ?";//框架，占位符4ps = conn.prepareStatement(sql);//编译5ps.setString(1,loginName);6ps.setString(2,loginPwd);7rs = ps.executeQuery();java

```xml
  <groupId>com.atguigu.maven</groupId>
  <artifactId>pro01-maven-java</artifactId>
  <version>1.0-SNAPSHOT</version>
```

在 Maven 仓库中生成的路径如下：

```log
D:\maven-rep1026\com\atguigu\maven\pro01-maven-java\1.0-SNAPSHOT\pro01-maven-java-1.0-SNAPSHOT.jar
```

1

另外，安装操作还会将 pom.xml 文件转换为 XXX.pom 文件一起存入本地仓库。所以我们在 Maven 的本地仓库中想看一个 jar 包原始的 pom.xml 文件时，查看对应 XXX.pom 文件即可，它们是名字发生了改变，本质上是同一个文件。

# 创建web工程

## [#](http://heavy_code_industry.gitee.io/code_heavy_industry/pro002-maven/chapter03/verse04.html#_2、操作)2、操作

注意：如果在上一个工程的目录下执行 mvn archetype:generate 命令，那么 Maven 会报错：不能在一个非 pom 的工程下再创建其他工程。所以不要再刚才创建的工程里再创建新的工程，**请回到工作空间根目录**来操作。

然后运行生成工程的命令：

mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-webapp -DarchetypeVersion=1.4

下面的操作按照提示执行：



## 8、配置对 servlet-api.jar 包的依赖

对于不知道详细信息的依赖可以到https://mvnrepository.com/网站查询。使用关键词搜索，然后在搜索结果列表中选择适合的使用。



P47,创建fact的步骤

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-war-plugin</artifactId>
            <version>3.3.1</version>
        </plugin>

    </plugins>
</build>
```

war打包出错  加入插件

```
<build>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-war-plugin</artifactId>
            <version>3.3.1</version>
        </plugin>

    </plugins>
</build>
```

### 高级

![image-20220729150359167](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220729150359167.png)

![image-20220729150407607](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220729150407607.png)

