## 为什么使用B+树

https://jaydenwen123.github.io/boltdb/

"E:\书\java路线书籍（代码随想录知识星球）\#115 数据存储与检索(20210527go夜读) (1).pdf"

保存数据的核心技术，也就是说，存储引擎是服务于存储服务的，通过存储引擎将数据保存。就跟计算机如何将数据保存到磁盘中一样，在数据库中，存储引擎的意思就是通过何种引擎将数据存储在磁盘中。

![image-20220822152802349](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822152802349.png)

![image-20220822153225064](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822153225064.png)

​	

![image-20220822154041847](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822154041847.png)

b+树，只有叶子节点存的才是数据，其他的是各种索引

![image-20220822154446934](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822154446934.png)

选择B+树的原因

多版本并发控制和隔离级别

![image-20220822090709103](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822090709103.png)

![image-20220822090857656](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822090857656.png)

![image-20220822162835519](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822162835519.png)

 



innodb有一个缓冲层![image-20220822091126352](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822091126352.png)

![image-20220822091230732](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822091230732.png)

![image-20220822091251207](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822091251207.png)

![image-20220822091457862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822091457862.png)

一般通过最近最少使用LRU 来管理

![image-20220822093507917](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822093507917.png)

有一个重做日志缓存![image-20220822093718269](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822093718269.png)

![image-20220822093847029](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822093847029.png)

![image-20220822094135707](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822094135707.png)

![image-20220822094324151](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822094324151.png)

动态修改后并没有保存

![image-20220822101619498](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822101619498.png)

![image-20220822102459592](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822102459592.png)

查询日志文件，默认也是不开启的

![image-20220822102723747](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822102723747.png)

![image-20220822103251144](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822103251144.png)

#### 表 

![image-20220822103439876](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822103439876.png)

![image-20220822103729559](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822103729559.png)

非空唯一作为索引

![image-20220822104031893](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822104031893.png)

![image-20220822104130125](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822104130125.png)

### 4.2-4.4

![image-20220822131340021](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822131340021.png)

先是分配32个分散的页，超过之后按64个叶64个页的分配

页是磁盘管理的最小空间

innodb是按照行存放数据的

行溢出数据---大数据存放在行之外

varchar  可以存放很长数据，因为row头部最多两个字节来标识这个字段的长度

16k 放不下那么多数据，所以同一个偏移量指示后面的存在了哪里（指向了行溢出页）

![image-20220822145831493](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822145831493.png)







![image-20220822113215976](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822113215976.png)

![image-20220822113258352](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822113258352.png)

![image-20220822150602335](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822150602335.png)

![image-20220822150635034](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822150635034.png)

![image-20220822151006259](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822151006259.png)

水平分区![image-20220822151438027](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822151438027.png)

![image-20220822151751788](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822151751788.png)

![image-20220822163859140](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822163859140.png)

![image-20220822164049323](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822164049323.png)

大部分分区分类都是RANGE分区

RANGE分区是实战最常用的一种分区类型，行数据基于属于一个给定的连续区间的列值被放入分区。

但是记住，**当插入的数据不在一个分区中定义的值的时候，会抛异常。**

RANGE分区主要用于日期列的分区，比如交易表啊，销售表啊等。可以根据年月来存放数据。

如果你分区走的唯一索引中date类型的数据，那么注意了，优化器只能对YEAR(),TO_DAYS(),TO_SECONDS(),UNIX_TIMESTAMP()这类函数进行优化选择。实战中可以用int类型，那么只用存yyyyMM就好了。也不用关心函数了。
如果创建了分区，那么不能直接删除全部的分区。删除表才能删除全部的分区，不然至少要留下一个分区"./。、"

![image-20220822180542652](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822180542652.png)

![image-20220822181015320](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822181015320.png)

簇妆存储：找4，根据索引可以找到那个簇：![image-20220822181225472](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822181225472.png)

怎样的粒度锁定数据？![image-20220822182256853](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822182256853.png)

![image-20220822184702771](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822184702771.png)

![image-20220822184906870](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822184906870.png)

![image-20220822185044899](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822185044899.png) 

lock in share   mode;    commit;

![image-20220822185419840](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822185419840.png)

![image-20220822190413529](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822190413529.png)

![image-20220822190706319](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822190706319.png)

**没有提交是不会产生一个快照版本的**

![image-20220822193419130](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822193419130.png)

![image-20220822193457915](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822193457915.png)

![image-20220822201812633](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822201812633.png)



![image-20220822205328654](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822205328654.png)

![image-20220822205543292](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822205543292.png)

**脏页：缓存中修改了，但是没有刷新到磁盘。    脏数据:事物对缓冲池进行修改，并且没有提交**

![image-20220822205800169](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822205800169.png)

![image-20220822213705704](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822213705704.png)

















##### 锁    [深入理解数据库行锁与表锁 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/52678870#:~:text=顾名思义，表锁就,后才能进行操作。)

当插入数据时，就锁定表，这叫做”锁表”；当更新数据时，就锁定行，这叫做”锁行”。

![preview](https://pic2.zhimg.com/v2-eec522a8cf7d8a38eaea29192edbb2f5_r.jpg)

![preview](https://pic3.zhimg.com/v2-5cf8b96fdca1428e6f3cce863fdfa73e_r.jpg)

mysql的**行锁是基于索引加载的**，所以行锁是要加在索引响应的行上，即命中索引：：找到要加锁的索引，然后对索引一致的加锁

当其他事务访问数据库同一张表时，被锁定的记录不能被访问，其他的记录都可以访问到。

行锁的特征：锁冲突概率低，并发性高，但是会有死锁的情况出现。**表锁响应的是非索引字段，即全表扫描**，全表扫描时锁定整张表，sql语句可以通过执行计划看出扫描了多少条记录。由于表锁每次都是锁一整张表，所以表锁的锁冲突几率特别高，表锁不会出现死锁的情况。

记录锁：记录锁锁的是表中的某一条记录，记录锁的出现条件**必须是精准命中索引并且索引是唯一索引**，如主键id，就像我们上面描述行锁时使用的sql语句图，在这里就挺适用的。

间隙锁又称之为区间锁，每次锁定都是锁定一个区间，隶属行锁。既然间隙锁隶属行锁，那么，间隙锁的触发条件必然是命中索引的，

间隙锁又称之为区间锁，每次锁定都是锁定一个区间，隶属行锁。既然间隙锁隶属行锁，那么，间隙锁的触发条件必然是命中索引的，当我们查询数据用范围查询而不是相等条件查询时，**查询条件命中索引**，并且**没有查询到符合条件的记录**，此时就会将查询条件中的范围数据进行锁定(即使是范围库中不存在的数据也会被锁定)，**间隙锁只会出现在可重复读的事务隔离级别中，**mysql的行锁默认就是使用的临键锁，临键锁是由记录锁和间隙锁共同实现的，上面我们学习间隙锁时，间隙锁的触发条件是命中索引，范围查询没有匹配到相关记录。而临键锁恰好相反，临键锁的触发条件也是**查询条件命中索引**，不过，临键锁**有匹配到数据库记录**；

#### 隔离级别

**Read Uncommitted（读取未提交内容）**

在该隔离级别，所有事务都可以看到其他未提交事务的执行结果。本隔离级别很少用于实际应用，因为它的性能也不比其他级别好多少。读取未提交的数据，也被称之为脏读（Dirty Read）。

**Read Committed（读取提交内容）**

这是大多数数据库系统的默认隔离级别（但不是MySQL默认的）。它满足了隔离的简单定义：一个事务只能看见已经提交事务所做的改变。这种隔离级别 也支持所谓的不可重复读（Nonrepeatable Read），因为同一事务的其他实例在该实例处理其间可能会有新的commit，所以同一select可能返回不同结果。

**Repeatable Read（可重读）**

这是MySQL的默认事务隔离级别，它确保同一事务的多个实例在并发读取数据时，会看到同样的数据行。不过理论上，这会导致另一个棘手的问题：幻读 （Phantom Read）。简单的说，幻读指当用户读取某一范围的数据行时，另一个事务又在该范围内插入了新行，当用户再读取该范围的数据行时，会发现有新的“幻影” 行。InnoDB和Falcon存储引擎通过多版本并发控制（MVCC，Multiversion Concurrency Control）机制解决了该问题。

**Serializable（可串行化）**

这是最高的隔离级别，它通过强制事务排序，使之不可能相互冲突，从而解决幻读问题。简言之，它是在每个读的数据行上加上共享锁。在这个级别，可能导致大量的超时现象和锁竞争。

这四种隔离级别采取不同的锁类型来实现，若读取的是同一个数据的话，就容易发生问题。例如：

脏读(Drity Read)：某个事务已更新一份数据，另一个事务在此时读取了同一份数据，由于某些原因，前一个RollBack了操作，则后一个事务所读取的数据就会是不正确的。

 

不可重复读(Non-repeatable read):在一个事务的两次查询之中数据不一致，这可能是两次查询过程中间插入了一个事务更新的原有的数据。

 

幻读(Phantom Read):在一个事务的两次查询中数据笔数不一致，例如有一个事务查询了几列(Row)数据，而另一个事务却在此时插入了新的几列数据，先前的事务在接下来的查询中，就会发现有几列数据是它先前所没有的。

 在可重复读隔离级别下，事务B只能在事务A修改过数据并提交后，自己也提交事务后，才能读取到事务B修改的数据。

因为有  undo log   回滚日志，所以可以读取快照内很久之前的数据

在MySQL中，实现了这四种隔离级别，分别有可能产生问题如下所示：

![img](https://img2018.cnblogs.com/blog/1646034/201904/1646034-20190430095830286-1397235000.png)

[彻底搞懂 MySQL 事务的隔离级别-阿里云开发者社区 (aliyun.com)](https://developer.aliyun.com/article/743691)

不可重复读;:：明明没有提交事务，却读到两次不一样的数据

#### 特性

![image-20220822212636091](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822212636091.png)

![image-20220822212639692](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822212639692.png)

![image-20220822212645438](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822212645438.png)





##### 事务分类

![image-20220822212909699](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822212909699.png)

![image-20220822213234300](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822213234300.png)

![image-20220822213427283](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220822213427283.png)

### 索引

[(32条消息) 一文搞懂MySQL索引（清晰明了）_Free Joe的博客-CSDN博客_mysql索引](https://blog.csdn.net/wangfeijiu/article/details/113409719)

索引分单列索引和组合索引。单列索引，即一个索引只包含单个列，一个表可以有多个单列索引，但这不是组合索引。组合索引，即一个索引包含多个列。创建索引时，你需要确保该索引是应用在 SQL 查询语句的条件(一般作为 WHERE 子句的条件)。

实际上，索引也是一张表，该表保存了主键与索引字段，并指向实体表的记录。

上面都在说使用索引的好处，但过多的使用索引将会造成滥用。因此索引也会有它的缺点：虽然索引大大提高了查询速度，同时却会降低更新表的速度，如对表进行INSERT、UPDATE和DELETE。因为更新表时，MySQL不仅要保存数据，还要保存一下索引文件。

建立索引会占用磁盘空间的索引文件。

create index indexname ON table_name (column_name)

alter table table_name ADD INDEX  indexname(column_name)

```sql
CREATE TABLE mytable(  
ID INT NOT NULL,   
username VARCHAR(16) NOT NULL,  
INDEX [indexName] (username(length))  
);  
DROP INDEX [indexName] ON mytable; 
#修改表结构
ALTER table mytable ADD UNIQUE [indexName] (username(length))
#创建表时直接指定
CREATE TABLE mytable(  
ID INT NOT NULL,  
username VARCHAR(16) NOT NULL,  
UNIQUE [indexName] (username(length))  
);  

```

- 索引大大减小了服务器需要扫描的数据量，从而大大加快数据的检索速度，这也是创建索引的最主要的原因。
- 索引可以帮助服务器避免排序和创建临时表
- 索引可以将随机IO变成顺序IO

**应该创建索引的列**
在经常需要搜索的列上，可以加快搜索的速度
在作为主键的列上，强制该列的唯一性和组织表中数据的排列结构
在经常用在连接（JOIN）的列上，这些列主要是一外键，可以加快连接的速度
在经常需要根据范围（<，<=，=，>，>=，BETWEEN，IN）进行搜索的列上创建索引，因为索引已经排序，其指定的范围是连续的
在经常需要排序（order by）的列上创建索引，因为索引已经排序，这样查询可以利用索引的排序，加快排序查询时间；
在经常使用在WHERE子句中的列上面创建索引，加快条件的判断速度。
**不该创建索引的列**
对于那些在查询中很少使用或者参考的列不应该创建索引。
若列很少使用到，因此有索引或者无索引，并不能提高查询速度。相反，由于增加了索引，反而降低了系统的维护速度和增大了空间需求。
对于那些只有很少数据值或者重复值多的列也不应该增加索引。
这些列的取值很少，例如人事表的性别列，在查询的结果中，结果集的数据行占了表中数据行的很大比例，即需要在表中搜索的数据行的比例很大。增加索引，并不能明显加快检索速度。
对于那些定义为text, image和bit数据类型的列不应该增加索引。
这些列的数据量要么相当大，要么取值很少。
当该列修改性能要求远远高于检索性能时，不应该创建索引。（修改性能和检索性能是互相矛盾的）

哈希索引就是采用一定的哈希算法，把键值换算成新的哈希值，检索时不需要类似B+树那样从根节点到叶子节点逐级查找，只需一次哈希算法即可立刻定位到相应的位置，速度非常快。Hash索引仅仅能满足`"=",“IN"和”<=>"`查询，不能使用范围查询。也不支持任何范围查询，

存储引擎为InnoDB：

*.frm：与表相关的元数据信息都存放在frm文件，包括表结构的定义信息等
*.ibd：InnoDB DATA，表数据和索引的文件。该表的索引(B+树)的每个非叶子节点存储索引，叶子节点存储索引和索引对应的数据

索引分类：{逻辑分类{z主键索引，唯一索引，普通索引，全文索引}   列数分类{单例索引，组合索引}  物理分类{聚簇索引和非聚簇索引}}聚簇是为了提高某个属性(或属性组)的查询速度，把这个或这些属性(称为聚簇码)上具有相同值的元组集中存放在连续的物理块聚簇索引（clustered index）不是单独的一种索引类型，而是一种数据存储方式。这种存储方式是依靠B+树来实现的，根据表的主键构造一棵B+树且B+树叶子节点存放的都是表的行记录数据时，方可称该主键索引为聚簇索引。只有InnoDB的主键索引才是聚簇索引，InnoDB中的辅助索引以及MyISAM使用的都是非聚簇索引。每张表最多只能拥有一个聚簇索引。

缺点：

插入速度严重依赖于插入顺序，按照主键的顺序插入是最快的方式，否则将会出现页分裂，严重影响性能。因此，对于InnoDB表，我们一般都会定义一个自增的ID列为主键（主键列不要选没有意义的自增列，选经常查询的条件列才好，不然无法体现其主键索引性能）
.更新主键的代价很高，因为将会导致被更新的行移动。因此，对于InnoDB表，我们一般定义主键为不可更新。
二级索引访问需要两次索引查找，第一次找到主键值，第二次根据主键值找到行数据。

# 面试题

![image-20220901154613052](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220901154613052.png)

[小破站高质量面试题：MySQL 夺命连环50问（高频面试题及解析）_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1ta411C7xq?spm_id_from=333.337.search-card.all.click&vd_source=14dd36e0ffe11b8a93626170e816f2d7)

