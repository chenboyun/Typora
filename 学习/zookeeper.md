xsync    同步分发脚本

选举机制![image-20220829100245522](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829100245522.png)

![image-20220829100625540](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829100625540.png)

jps(Java Virtual Machine Process Status Tool)

是java提供的一个显示当前所有java进程pid的命令，适合在linux/unix平台上简单察看当前java进程的一些简单情况。

很多人都是用过unix系统里的ps命令，这个命令主要是用来显示当前系统的进程情况，有哪些进程以及进程id。

**带序号节点可以重复，因为自增的序号保证不重复**

**持久节点和短暂节点： -e    重启后是否消失**

##### 监听器原理：

![image-20220829102222156](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829102222156.png)

连接器告诉监听器，我要监听哪个![image-20220829102310892](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829102310892.png)

注册一次，生效一次，

半数机制的写操作![image-20220829113222010](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829113222010.png)

![image-20220829113346645](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829113346645.png)

对于zookeeper来说，都是客户，服务器是创建节点，而客户机是监听![image-20220829113738122](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829113738122.png)

