

[Redis | ZC 的学习录 (zhangc233.github.io)](https://zhangc233.github.io/2021/05/02/Redis/)

《Redis设计与实现》

nosql  not only sql

![image-20220728095435570](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220728095435570.png)

写配置文件，然后通过配置文件（当做参数传入）打开，就可以后台启动

客户端链接   redis-lis

exit   退出  shutdown

redis 是单线程+多路IO复用技术

set k1 xyq    

keys *              get k1

exists k1    type k1  del key  

unlink key   根据value 选择非阻塞删除（异步删除、慢慢删除）

expire k1  10  存活时间设置为10秒    ttl k1  查看还有多少过期   -1 永不过期，-2已过期

select 切换数据库     dbsize  查看数据库key的数量

flushdb  清空当前库

flushall  通杀全部数据库

append  追加      strlen  长度   setnx   当不存在时才操作



整合redis6（springboot）

![image-20220728181250528](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220728181250528.png)

redis 的 事物和MySQL不一样，他的目的是让命令形成一个序列化，不能插队；不保证原子性；没有提交前都不会被执行

lua  洛脚本语言

RDB   redis database

AOF   append only file

slaveof no one

缓存穿透：

![image-20220729121500752](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220729121500752.png)

缓存击穿





![image-20220805225233201](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220805225233201.png)

![image-20220805225355151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220805225355151.png)

多个端口可以：redis-cli     -p 6379

多实例关闭，指定端口关闭：redis-cli -p 6379 shutdown

  默认16个数据库，类似数组下标从0开始，初始默认使用0号库使用命令 select  <dbid>来切换数据库。如: select 8 统一密码管理，所有库同样密码。dbsize查看当前数据库的key的数量flushdb清空当前库flushall通杀全部库

Redis是单线程+多路IO复用技术

#### ***\*Redis\*******\*键\*******\*(key)\****

keys *查看当前库所有key   (匹配：keys *1)

exists key判断某个key是否存在

type key 查看你的key是什么类型

del key    删除指定的key数据

unlink key  根据value选择非阻塞删除

仅将keys从keyspace元数据中删除，真正的删除会在后续异步操作。

expire key 10  10秒钟：为给定的key设置过期时间

ttl key 查看还有多少秒过期，-1表示永不过期，-2表示已过期

 

select命令切换数据库

dbsize查看当前数据库的key的数量

flushdb清空当前库

flushall通杀全部库



##### 

#### string

String类型是二进制安全的。意味着Redis的string可以包含任何数据。比如jpg图片或者序列化的对象。

get  <key>查询对应键值

append  <key><value>将给定的<value> 追加到原值的末尾

strlen  <key>获得值的长度

setnx  <key><value>只有在 key 不存在时   设置 key 的值

 

incr  <key>

将 key 中储存的数字值增1

只能对数字值操作，如果为空，新增值为1

decr  <key>

将 key 中储存的数字值减1

只能对数字值操作，如果为空，新增值为-1

incrby / decrby  <key><步长>将 key 中储存的数字值增减。自定义步长。

（1）在单线程中， 能够在单条指令中完成的操作都可以认为是"原子操作"，因为中断只能发生于指令之间。

（2）在多线程中，不能被其它进程（线程）打断的操作就叫原子操作。

Redis单命令的原子性主要得益于Redis的单线程。

mset  <key1><value1><key2><value2>  ..... 

同时设置一个或多个 key-value对  

mget  <key1><key2><key3> .....

同时获取一个或多个 value  

msetnx <key1><value1><key2><value2>  ..... 

同时设置一个或多个 key-value 对，当且仅当所有给定 key 都不存在。

getrange  <key><起始位置><结束位置>

获得值的范围，类似java中的substring，***\*前包，后包\****

setrange  <key><起始位置><value>

用 <value>  覆写<key>所储存的字符串值，从<起始位置>开始(***\*索引从0开始\****)。

 

***\*setex  <key><过期时间\*******\*><value>\****

设置键值的同时，设置过期时间，单位秒。

getset <key><value>

以新换旧，设置了新值同时获得旧值。

采用预分配冗余空间的方式来减少内存的频繁分配.

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml10236\wps2.jpg) 

如图中所示，内部为当前字符串实际分配的空间capacity一般要高于实际字符串长度len。当字符串长度小于1M时，扩容都是加倍现有的空间，如果超过1M，扩容时一次只会多扩1M的空间。需要注意的是字符串最大长度为512M。

#### List

底层实际是个双向链表，push  pop(加上l   r  的前缀)

lrange <key><start><stop>

按照索引下标获得元素(从左到右)

lrange mylist 0 -1  0左边第一个，-1右边第一个，（0-1表示获取所有）

lindex <key><index>按照索引下标获得元素(从左到右)

llen <key>获得列表长度 linsert <key>  before <value><newvalue>在<value>的后面插入<newvalue>插入值

lrem <key><n><value>从左边删除n个value(从左到右)

lset<key><index><value>将列表key下标为index的值替换成value

List的数据结构为快速链表quickList。

首先在列表元素较少的情况下会使用一块连续的内存存储，这个结构是ziplist，也即是压缩列表。

它将所有的元素紧挨着一起存储，分配的是一块连续的内存。

当数据量比较多的时候才会改成quicklist。

因为普通的链表需要的附加指针空间太大，会比较浪费空间。比如这个列表里存的只是int类型的数据，结构上还需要两个额外的指针prev和next。



#### set

Redis set对外提供的功能与list类似是一个列表的功能，特殊之处在于set是可以***\*自动排重\****的，当你需要存储一个列表数据，又不希望出现重复数据时，set是一个很好的选择，并且set提供了判断某个成员是否在一个set集合内的重要接口，这个也是list所不能提供的。

Redis的Set是string类型的无序集合。它底层其实是一个value为null的hash表，所以添加，删除，查找的***\*复杂度都是O(1)\****。

一个算法，随着数据的增加，执行时间的长短，如果是O(1)，数据增加，查找数据的时间不变

sadd

smembers <key>取出该集合的所有值。

sismember <key><value>判断集合<key>是否为含有该<value>值，有1，没有0

scard<key>返回该集合的元素个数。

spop <key>***\*随机从该集合中吐出一个值。\****

srandmember <key><n>随机从该集合中取出n个值。不会从集合中删除 。

smove <source><destination>value把集合中一个值从一个集合移动到另一个集合

sinter <key1><key2>返回两个集合的交集元素。

sunion <key1><key2>返回两个集合的并集元素。

sdiff <key1><key2>返回两个集合的***\*差集\****元素(key1中的，不包含key2中的)

#### hash

Java中HashSet的内部实现使用的是HashMap，只不过所有的value都指向同一个对象。Redis的set结构也是一样，它的内部也使用hash结构，所有的value都指向同一个内部值。

Redis hash是一个string类型的field和value的映射表，hash特别适合用于存储对象。

类似Java里面的Map<String,Object>

![image-20220805234725263](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220805234725263.png)

Hash类型对应的数据结构是两种：ziplist（压缩列表），hashtable（哈希表）。当field-value长度较短且个数较少时，使用ziplist，否则使用hashtable。

#### zset

zadd  <key><score1><value1><score2><value2>…

将一个或多个 member 元素及其 score 值加入到有序集 key 当中。

***\*zrange <key><start><stop>  [WITHSCORES]\****  

返回有序集 key 中，下标在<start><stop>之间的元素

带WITHSCORES，可以让分数一起和值返回到结果集。

zrangebyscore key minmax [withscores] [limit offset count]

返回有序集 key 中，所有 score 值介于 min 和 max 之间(包括等于 min 或 max )的成员。有序集成员按 score 值递增(从小到大)次序排列。 

zrevrangebyscore key maxmin [withscores] [limit offset count]        

同上，改为从大到小排列。 

zincrby <key><increment><value>    为元素的score加上增量

zrem  <key><value>删除该集合下，指定值的元素 

zcount <key><min><max>统计该集合，分数区间内的元素个数 

zrank <key><value>返回该值在集合中的排名，从0开始。

#### Bitmap

可以把Bitmaps想象成一个以位为单位的数组， 数组的每个单元只能存储0和1，

setbit<key><offset><value>设置Bitmaps中某个偏移量的值（0或1）

getbit<key><offset>获取Bitmaps中某个偏移量的值

bitcount<key>[start end] 统计字符串从start字节到end字节比特值为1的数量

但Bitmaps并不是万金油， 假如该网站每天的独立访问用户很少， 例如只有10万（大量的僵尸用户） ， 那么两者的对比如下表所示， 很显然， 这时候使用Bitmaps就不太合适了， 因为基本上大部分位都是0。

#### 事务

Redis事务的主要作用就是串联多个命令防止别的命令插队。从输入Multi命令开始，输入的命令都会依次进入命令队列中，但不会执行，直到输入Exec后，Redis会将之前的命令队列中的命令依次执行。

组队的过程中可以通过discard来放弃组队。  组队中某个命令出现了报告错误，执行时整个的所有队列都会被取消。如果执行阶段某个命令报出了错误，则只有报错的命令不会被执行，而其他的命令都会执行，不会回滚。

***\*悲观锁\****

就是很悲观，每次去拿数据的时候都认为别人会修改，所以每次在拿数据的时候都会上锁

***\*乐观锁(Optimistic Lock)\*******\*,\**** 顾名思义，就是很乐观，每次去拿数据的时候都认为别人不会修改，所以不会上锁，但是在更新的时候会判断一下在此期间别人有没有去更新这个数据，可以使用版本号等机制。***\*乐观锁适用于多读的应用类型，这样可以提高吞吐量\****。

在执行multi之前，先执行watch key1 [key2],可以监视一个(或多个) key ，如果在事务***\*执行之前这个(或这些) key 被其他命令所改动，那么事务将被打断。\****

***\*R\*******\*edis\*******\*事务三特性\****

Ø 单独的隔离操作 

n 事务中的所有命令都会序列化、按顺序地执行。事务在执行的过程中，不会被其他客户端发送来的命令请求所打断。 

Ø 没有隔离级别的概念 

n 队列中的命令没有提交之前都不会实际被执行，因为事务提交前任何指令都不会被实际执行

Ø 不保证原子性 

n 事务中如果有一条命令执行失败，其后的命令仍然会被执行，没有回滚 

LUA脚本是类似redis事务，有一定的原子性，不会被其他命令插队，可以完成一些redis事务性的操作。

#### 持久化

Redis 提供了2个不同形式的持久化方式。

l RDB（Redis DataBase）

l AOF（Append Of File）

在指定的时间间隔内将内存中的数据集快照写入磁盘， 也就是行话讲的Snapshot快照，它恢复时是将快照文件直接读到内存里

Redis会单独创建（fork）一个子进程来进行持久化，会先将数据写入到 一个临时文件中，待持久化过程都结束了，再用这个临时文件替换上次持久化好的文件。 整个过程中，主进程是不进行任何IO操作的，这就确保了极高的性能 如果需要进行大规模数据的恢复，且对于数据恢复的完整性不是非常敏感，那RDB方式要比AOF方式更加的高效。***\*RDB的缺点是\*******\*最后一次持久化后的数据可能丢失\****。

![image-20220806084934290](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220806084934290.png)

l Fork的作用是复制一个与当前进程一样的进程。新进程的所有数据（变量、环境变量、程序计数器等） 数值都和原进程一致，但是是一个全新的进程，并作为原进程的子进程

l 在Linux程序中，fork()会产生一个和父进程完全相同的子进程，但子进程在此后多会exec系统调用，出于效率考虑，Linux中引入了“***\*写时复制技术\****”

**l** ***\*一般情况父进程和子进程会共用同一段物理内存\****，只有进程空间的各段的内容要发生变化时，才会将父进程的内容复制一份给子进程。

save ：save时只管保存，其它不管，全部阻塞。手动保存。不建议。

***\*bgsave：\*******\*Redis\*******\*会在后台异步进行快照操作， 快照同时还可以响应客户端请求。\****

可以通过lastsave 命令获取最后一次成功执行快照的时间

save ：save时只管保存，其它不管，全部阻塞。手动保存。不建议。

***\*bgsave：\*******\*Redis\*******\*会在后台异步进行快照操作， 快照同时还可以响应客户端请求。\****

可以通过lastsave 命令获取最后一次成功执行快照的时间

l 适合大规模的数据恢复

l 对数据完整性和一致性要求不高更适合使用

l 节省磁盘空间

l 恢复速度快

***\*劣势\****

l Fork的时候，内存中的数据被克隆了一份，大致2倍的膨胀性需要考虑

l 虽然Redis在fork时使用了***\*写时拷贝技术\****,但是如果数据庞大时还是比较消耗性能。

在备份周期在一定间隔时间做一次备份，所以如果Redis意外down掉的话，就会丢失最后一次快照后的所有修改

***\*AOF持久化流程\****

（1）客户端的请求写命令会被append追加到AOF缓冲区内；

（2）AOF缓冲区根据AOF持久化策略[always,everysec,no]将操作sync同步到磁盘的AOF文件中；

（3）AOF文件大小超过重写策略或手动重写时，会对AOF文件rewrite重写，压缩AOF文件容量；

（4）Redis服务重启时，会重新load加载AOF文件中的写操作达到数据恢复的目的；

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml10236\wps4.jpg) 

AOF和RDB同时开启，系统默认取AOF的数据（数据不会存在丢失）

1是什么：

AOF采用文件追加方式，文件会越来越大为避免出现此种情况，新增了重写机制, 当AOF文件的大小超过所设定的阈值时，Redis就会启动AOF文件的内容压缩， 只保留可以恢复数据的最小指令集.可以使用命令bgrewriteaof

2重写原理，如何实现重写

AOF文件持续增长而过大时，会fork出一条新进程来将文件重写(也是先写临时文件最后再rename)，redis4.0版本后的重写，是指上就是把rdb 的快照，以二级制的形式附在新的aof头部，作为已有的历史数据，替换掉原来的流水账操作。

3、重写流程

（1）bgrewriteaof触发重写，判断是否当前有bgsave或bgrewriteaof在运行，如果有，则等待该命令结束后再继续执行。

（2）主进程fork出子进程执行重写操作，保证主进程不会阻塞。

（3）子进程遍历redis内存中数据到临时文件，客户端的写请求同时写入aof_buf缓冲区和aof_rewrite_buf重写缓冲区保证原AOF文件完整以及新AOF文件生成期间的新的数据修改动作不会丢失。

（4）1).子进程写完新的AOF文件后，向主进程发信号，父进程更新统计信息。2).主进程把aof_rewrite_buf中的数据写入到新的AOF文件。

（5）使用新的AOF文件覆盖旧的AOF文件，完成AOF重写。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml10236\wps5.png)

n 备份机制更稳健，丢失数据概率更低。

n 可读的日志文本，通过操作AOF稳健，可以处理误操作。

***\*劣势\****

n 比起RDB占用更多的磁盘空间。

n 恢复备份速度要慢。

n 每次读写都同步的话，有一定的性能压力。

n 存在个别Bug，造成恢复不能。

主机数据更新后根据配置和策略， 自动同步到备机的master/slaver机制，***\*Master以写为主，\*******\*Slave\*******\*以读为主\****

***\*能干嘛\****

l 读写分离，性能扩展

l 容灾快速恢复



主从机：配从不配主

slaveof  <ip><port>

成为某个实例的从服务器

1、在6380和6381上执行: slaveof 127.0.0.1 6379



***\*复制原理\****

l Slave启动成功连接到master后会发送一个sync命令

l Master接到命令启动后台的存盘进程，同时收集所有接收到的用于修改数据集命令， 在后台进程执行完毕之后，master将传送整个数据文件到slave,以完成一次完全同步

l 全量复制：而slave服务在接收到数据库文件数据后，将其存盘并加载到内存中。

l 增量复制：Master继续将新的所有收集到的修改命令依次传给slave,完成同步

l 但是只要是重新连接master,一次完全同步（全量复制)将被自动执行

哨兵模式：***\*反客为主的自动版\****，能够后台监控主机是否故障，如果故障了根据投票数自动将从库转换为主库

![image-20220806093418141](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220806093418141.png)

![image-20220806094321246](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220806094321246.png)

***\*什么是\*******\*slots\****

***\*[OK] All nodes agree about slots configuration.\****

***\*>>> Check for open slots...\****

***\*>>> Check slots coverage...\****

***\*[OK] All\**** ***\*16384\**** ***\*slots covered.\****

一个 Redis 集群包含 16384 个插槽（hash slot）， 数据库中的每个键都属于这 16384 个插槽的其中一个， 

不在一个slot下的键值，是不能使用mget,mset等多键操作。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml10236\wps6.png) 

可以通过{}来定义组的概念，从而使key中{}内相同内容的键值对放到一个slot中去。

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml10236\wps7.png)

即使连接的不是主机，集群会自动切换主机存储。主机写，从机读。

无中心化主从集群。无论从哪台主机写的数据，其他主机上都能读到数据。

实现扩容

分摊压力

无中心配置相对简单

多键操作是不被支持的 

多键的Redis事务是不被支持的。lua脚本不被支持