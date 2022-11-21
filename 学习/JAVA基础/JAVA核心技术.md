## 第八章 泛型程序设计

 



## 第九章  集合

声明为上层，然后实现为下层，这样想要修改时只需要换一个实现（实例），不需要修改代码

Iterator 迭代器，可以访问集合中的元素(他也是接口)

Iterator<E> iterator()            has methods:

![image-20220428160141332](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220428160141332.png)

JAVA集合框架中的所有集合都必须有一个迭代器

```java
Collection<String> c =...
  Iterator<String> iter = c.iterator();
while (iter.hasNext()){
  String element = iter.next();
  dosomething 
}//for each 循环会编译成这种使用显式迭代器的循环
```

Collection 是 iterator ，所有iterator 都可以使用 iterator ;

有的迭代器并不是循序访问，你只知道最终会访问完所有元素

迭代器并不是指向元素，而是指向元素之间

int size()    他会提供**集合**的大小

boolean isEmpty()

boolean contains()

map 并不是  collection   collection 有子接口{

set  元素不能重复{Sortedset  会按顺序访问迭代器}

list  会记住元素的位置{可以使用整数索引进行访问

Java 把 LinkedList 当做 List  所以需要逐个寻找，并且 ArrayList 和他归为一个类 ，都是 List,}

queue

}

获得一个List  的 ListIterator 时，实际上获得的是他的子接口 ListIterator(可以正向反向访问列表)

最重要的几个接口(ArrayList    LinkedList  HashSet   TreeSet  HashMap,TreeMap ){

ArrayList    :移动起来很慢，可以随机访问，基本不需要迭代器

LinkedList  ：删除移动很容易；已经可以检测并发修改：}

List.of(3,5,,8,8,8,8,4,5,5)总是返回不可变的对象

![image-20220428171726213](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220428171726213.png)

Set（会拒绝重复）{

散列集：HashMap用了散列码后可以找到一个桶> 他是拥有相同散列码的不同元素，散列函数不好会影响性能

树集：慢/保证性能总是很好；元素必须是可比较的，有可能找不到比较的方法

}

#### 队列：

队列：一个简单的队列：LinkedList  （extends Queue）

双端队列

优先队列：删除最高优先级的数;PriorityQueue

#### 映射收集键与值{

HashMap  ：无序：按散列组织键{put   get  getOrElse   remove(key)    forEach(k,v)//之后就使用 v,k    getOrDefault(word,0)

putIfAbsent （word,0）(当且仅当以前没有这个值的时候会放入一个0)    merge(word,1,Integer::sum )(接受你想要查找的键，与现有值希望合并的那个值，合并的函数)}

TreeMap: 有序；按顺序组织键

映射不是集合，但是会用到集合，映射的所有键是一个set  因为键是唯一的；一个映射的值是Collection 因为值可能不唯一；键值对构成set称为条目集；访问所有的键和值：  keySet

条目有一个奇怪的类型：Map.Entry  <String,Employee> entry : staff.entrySet()           Entry有 方法{getKey()   getValue()}  有一个相似的：   staff.forEach((k,v)-> do something whit k,v)

keyset （提供键的一个视图，而不是单独的集合） values   entrySet 生成集合是真正的的集合 }

LinkedHahMap  使用了额外的链接集来记住插入顺序，可以按照插入顺序访问元素    视图是列表的子范围

不可修改的视图：

使用集合常见的算法：

collections.min   collections.max  collections.fill

方法调用的一个优点是：别人一看就知道你要干什么 

![image-20220428190604308](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220428190604308.png)

![image-20220428190722270](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220428190722270.png)

![image-20220428190915741](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220428190915741.png)
