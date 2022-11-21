Python 的 3.0 版本，常被称为 Python 3000，或简称 Py3k。相对于 Python 的早期版本，这是一个较大的升级。为了不带入过多的累赘，Python 3.0 在设计的时候没有考虑向下兼容。

## 标识符

- 第一个字符必须是字母表中字母或下划线 **_** 。
- 标识符的其他的部分由字母、数字和下划线组成。
- 标识符对大小写敏感。

注释：

Python中单行注释以 **#** 开头

''' 第三注释 第四注释 '''  """ 第五注释 第六注释 """

使用缩进来表示代码块，不需要使用大括号 **{}** 。

Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠 **\** 来实现多行语句

在 [], {}, 或 () 中的多行语句，不需要使用反斜杠 **\**

- **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- **bool** (布尔), 如 True。
- **float** (浮点数), 如 1.23、3E-2
- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j

- Python 中的字符串不能改变。

- Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。

- 

- ```
  paragraph = """这是一个段落，
  可以由多行组成"""
  ```

Python 可以在同一行中使用多条语句，语句之间使用分号 **;** 分割

缩进相同的一组语句构成一个代码块，我们称之代码组。

像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。

我们将首行及后面的代码组称为一个子句(clause)。

```python
if expression : 
   suite
elif expression : 
   suite 
else : 
   suite
```

## import 与 from...import

在 python 用 **import** 或者 **from...import** 来导入相应的模块。

将整个模块(somemodule)导入，格式为： **import somemodule**

从某个模块中导入某个函数,格式为： **from somemodule import somefunction**

从某个模块中导入多个函数,格式为： **from somemodule import firstfunc, secondfunc, thirdfunc**

将某个模块中的全部函数导入，格式为： **from somemodule import \***

import sys

Python3 的六个标准数据类型中：

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；

- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

- 内置的 type() 函数可以用来查询变量所指的对象类型。  type(a)   type(b)

- isinstance(a, int)

- type()不会认为子类是一种父类类型。

- isinstance()会认为子类是一种父类类型。

- 

- ```
  del var_a, var_b
  ```

、Python可以同时为多个变量赋值，如a, b = 1, 2。

数值的除法包含两个运算符：**/** 返回一个浮点数，**//** 返回一个整数。

![image-20220906120830116](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220906120830116.png)

Python 没有单独的字符类型，一个字符就是长度为1的字符串。

Python 字符串不能被改变。向一个索引位置赋值，比如word[0] = 'm'会导致错误。

列表是写在方括号 **[]** 之间、用逗号分隔开的元素列表。

和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表。

List中的元素是可以改变的。

元组（tuple）与列表类似，不同之处在于元组的元素不能修改。元组写在小括号 **()** 里，元素之间用逗号隔开。tuple = ( 'abcd', 786 , 2.23, 'runoob', 70.2 )**print** (tuple[1:3])     # 输出从第二个元素开始到第三个元素
**print** (tuple[2:])     # 输出从第三个元素开始的所有元素构造包含 0 个或 1 个元素的元组比较特殊，所以有一些额外的语法规则：

```
tup1 = ()    # 空元组
tup2 = (20,) # 一个元素，需要在元素后添加逗号
```

以使用大括号 **{ }** 或者 **set()** 函数创建集合，注意：创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典。

创建格式：

```
parame = {value01,value02,...}
或者
set(value)
```

字典当中的元素是通过键来存取的，而不是通过偏移存取。

字典是一种映射类型，字典用 **{ }** 标识，它是一个无序的 **键(key) : 值(value)** 的集合。键(key)必须使用不可变类型。

在同一个字典中，键(key)必须是唯一的

dict = {}
dict['one'] = "1 - 菜鸟教程"
dict[2]   = "2 - 菜鸟工具"

tinydict = {'name': 'runoob','code':1, 'site': 'www.runoob.com'}

推倒式multiples = [i **for** i **in** range(30) **if** i % 3 == 0]

字典推导式;{ key_expr: value_expr for value in collection if condition }     newdict = {key:len(key) **for** key **in** listdemo}

| //   | 取整除 - 向下取接近商的整数                                  |
| ---- | ------------------------------------------------------------ |
| :=   | 海象运算符，可在表达式内部为变量赋值。  if (n := len(a)) > 10: |
|      |                                                              |

| and  | x and y                                             | 布尔"与" - 如果 x 为 False，x and y 返回 x 的值，否则返回 y 的计算值。 | (a and b) 返回 20。     |
| ---- | --------------------------------------------------- | ------------------------------------------------------------ | ----------------------- |
| or   | x or y                                              | 布尔"或" - 如果 x 是 True，它返回 x 的值，否则它返回 y 的计算值。 | (a or b) 返回 10。      |
| not  | not x                                               | 布尔"非" - 如果 x 为 True，返回 False 。如果 x 为 False，它返回 True。 | not(a and b) 返回 False |
| in   | 如果在指定的序列中找到值返回 True，否则返回 False。 | x 在 y 序列中 , 如果 x 在 y 序列中返回 True。                |                         |
| is   | is 是判断两个标识符是不是引用自一个对象             | **x is y**, 类似 **id(x) == id(y)** , 如果引用的是同一个对象则返回 True，否则返回 False |                         |

# number操作

| [abs(x)](https://www.runoob.com/python3/python3-func-number-abs.html) | 返回数字的绝对值，如abs(-10) 返回 10        |
| ------------------------------------------------------------ | ------------------------------------------- |
| [ceil(x)](https://www.runoob.com/python3/python3-func-number-ceil.html) | 返回数字的上入整数，如math.ceil(4.1) 返回 5 |

删除列表元素del list[2]

​    

| [list.append(obj)](https://www.runoob.com/python3/python3-att-list-append.html) 在列表末尾添加新的对象 |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ list(seq)](https://www.runoob.com/python3/python3-att-list-list.html) 将元组转换为列表 | [list.count(obj)](https://www.runoob.com/python3/python3-att-list-count.html) 统计某个元素在列表中出现的次数 |
| [ len(list)](https://www.runoob.com/python3/python3-att-list-len.html) 列表元素个数 | [list.extend(seq)](https://www.runoob.com/python3/python3-att-list-extend.html) 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表） |
|                                                              | [list.index(obj)](https://www.runoob.com/python3/python3-att-list-index.html) 从列表中找出某个值第一个匹配项的索引位置 |

访问字典里面的值：    tinydict['key']

tinydict['Age'] = 8               # 更新 Age tinydict['School'] = "菜鸟教程"  # 添加信息 

键必须不可变，所以可以用数字，字符串或元组充当，而用列表就不行，

创建一个空集合必须用 **set()** 而不是 **{ }**，因为 **{ }** 是用来创建一个空字典。

```
parame = {value01,value02,...}
或者
set(value)
 a = set('abracadabra')
 有一个方法，也可以添加元素，且参数可以是列表，元组，字典等  s.update( x )
 thisset.update({1,3})  //添加了1  和  3
 s.remove( x )//将元素 x 从集合 s 中移除，如果元素不存在，则会发生错误。
 s.discard( x )//除集合中的元素，且如果元素不存在，不会发生错误。
```

关键字end可以用于将结果输出到同一行，或者在输出的末尾添加不同的字符    print(b, end=',')

控制语句：

```python
if condition_1:
    statement_block_1
elif condition_2:
    statement_block_2
else:
    statement_block_3
    #每个条件后面要使用冒号 :，表示接下来是满足条件后要执行的语句块。
if age <= 0:
    print("你是在逗我吧!")
elif age == 1:
    print("相当于 14 岁的人。")
elif age == 2:
    print("相当于 22 岁的人。")
elif age > 2:
    human = 22 + (age -2)*5
    print("对应人类年龄: ", human)
    
while counter <= n:
    sum = sum + counter
    counter += 1
    
expr 条件语句为 true 则执行 statement(s) 语句块，如果为 false，则执行 additional_statement(s)。
count = 0
while count < 5:
   print (count, " 小于 5")
   count = count + 1
else:
   print (count, " 大于或等于 5")
    
    
for x in languages:
...     print (x)

你也可以使用range指定区间的值：
for i in range(5):     0 1 2 3 4 5 
for i in range(5,9) :     5 6 7 8 9
for i in range(0, 10, 3) :   0 3 6 9
a = ['Google', 'Baidu', 'Runoob', 'Taobao', 'QQ']
>>> for i in range(len(a)):
...     print(i, a[i])

还可以使用range()函数来创建一个列表：  list(range(5)) 0 1 2 3 4
```

pass 不做任何事情，一般用做占位语句，如下实例

迭代器

迭代器有两个基本的方法：**iter()** 和 **next()**。

字符串，列表或元组对象都可用于创建迭代器：

## 实例(Python 3.0+)

\>>> list=[1,2,3,4]
\>>> it = iter(list)   # 创建迭代器对象
\>>> **print** (next(it))  # 输出迭代器的下一个元素
1
\>>> **print** (next(it))
可以用for循环



for x in it:    print (x, end=" ")

StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况

```py
def __next__(self):
    if self.a <= 20:
      x = self.a
      self.a += 1
      return x
    else:
      raise StopIteration
      
```

##### 函数

- 函数代码块以 **def** 关键词开头，后接函数标识符名称和圆括号 **()**。

**def** hello() :
  **print**("Hello World!")

```
a=[1,2,3]

a="Runoob"
```

以上代码中，**[1,2,3]** 是 List 类型，**"Runoob"** 是 String 类型，而变量 a 是没有类型，她仅仅是一个对象的引用（一个指针），可以是指向 List 类型对象，也可以是指向 String 类型对象。

以下实例中演示了函数参数的使用不需要使用指定顺序：

```py
def printinfo( name, age ):
  printinfo( age=50, name="runoob" )
```

加了星号 ***** 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数。

```py
def printinfo( arg1, *vartuple ):
   "打印任何传入的参数"
   print ("输出: ")
   print (arg1)
   print (vartuple)
 
# 调用printinfo 函数
printinfo( 70, 60, 50 )


加了两个星号 ** 的参数会以字典的形式导入。
def printinfo( arg1, **vardict ):
printinfo(1, a=2,b=3)

声明函数时，参数中星号 * 可以单独出现，例如:

def f(a,b,*,c):
    return a+b+c
如果单独出现星号 *，则星号 * 后的参数必须用关键字传入：
 def f(a,b,*,c):
...     return a+b+c
... 
 f(1,2,3)   # 报错
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
TypeError: f() takes 2 positional arguments but 3 were given
f(1,2,c=3) # 正常
```

##### 内联函数

```
lambda [arg1 [,arg2,.....argn]]:expression
x = lambda a : a + 10
```

我们可以将匿名函数封装在一个函数内，这样可以使用同样的代码来创建多个匿名函数。

#### IO

```PY
str = input("请输入：")
print "你输入的内容是: ", str
input 可以接收一个Python表达式作为输入，并将运算结果返回。
打开文件
file object = open(file_name [, access_mode][, buffering])
一个文件被打开后，你有一个file对象，你可以得到有关该文件的各种信息。
print "是否已关闭 : ", fo.closed
fileObject.close()
fileObject.write(string)
fileObject.read([count])
str = fo.read(10)
import os
os.rename(current_file_name, new_file_name)
os.remove(file_name)
os.mkdir("newdir")
getcwd()方法显示当前的工作目录。   os.getcwd
mdir()方法删除目录，目录名称以参数传递。在删除这个目录之前，它的所有内容应该先被清除。
```

#### 类

```py
def __init__(self, name, salary):
      self.name = name
      self.salary = salary
      Employee.empCount += 1
__init__()方法是一种特殊的方法，被称为类的构造函数或初始化方法，当创建了这个类的实例时就会调用该方法
self 代表类的实例，self 在定义类的方法时是必须有的，虽然在调用时不必传入相应的参数。
self代表类的实例，而非类
类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self。
"创建 Employee 类的第一个对象"
emp1 = Employee("Zara", 2000)
hasattr(emp1, 'age')    # 如果存在 'age' 属性返回 True。
getattr(emp1, 'age')    # 返回 'age' 属性的值
setattr(emp1, 'age', 8) # 添加属性 'age' 值为 8
delattr(emp1, 'age')    # 删除属性 'age'
析构函数 __del__ ，__del__在对象销毁的时候被调用，当对象不再被使用时，__del__方法运行：
   def __del__(self):
      class_name = self.__class__.__name__
      print class_name, "销毁"
      
      继承的基类列表跟在类名之后，如下所示：

class SubClassName (ParentClass1[, ParentClass2, ...]):
  
  类的私有属性
__private_attrs：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 self.__private_attrs。
类的私有方法
__private_method：两个下划线开头，声明该方法为私有方法，不能在类的外部调用。在类的内部调用 self.__private_methods
print counter.__secretCount  # 报错，实例不能访问私有变量
```

##### 正则表达式

re.match 尝试从字符串的起始位置匹配一个模式，如果不是起始位置匹配成功的话，match() 就返回 none。

**函数语法**：

```
re.match(pattern, string, flags=0)
```

#### 数据库

```py
import MySQLdb

# 打开数据库连接
db = MySQLdb.connect("localhost", "testuser", "test123", "TESTDB", charset='utf8' )

# 使用cursor()方法获取操作游标 
cursor = db.cursor()
sql = '''       '''

try:
   # 执行sql语句
   cursor.execute(sql)
  results = cursor.fetchall()
   for row in results:
      fname = row[0]
   # 提交到数据库执行
   db.commit()
except:
   # 发生错误时回滚
   db.rollback()
# 关闭数据库连接
db.close()

#fetchone(): 该方法获取下一个查询结果集。结果集是一个对象
#fetchall():接收全部的返回结果行.
#rowcount: 这是一个只读属性，并返回执行execute()方法后影响的行数。
```

```py

mydb = mysql.connector.connect(
    host="localhost",
    user="root",
    passwd="123456",
    database="testdb",
    auth_plugin='mysql_native_password'
)
mycursor = mydb.cursor()
mycursor.execute("CREATE TABLE sites (name VARCHAR(255), url VARCHAR(255))")

#插入
sql = "INSERT INTO sites (name, url) VALUES (%s, %s)"
val = ("RUNOOB", "https://www.runoob.com")
mycursor.execute(sql, val)
#批量插入使用 executemany() 方法，该方法的第二个参数是一个元组列表，包含了我们要插入的数据：
sql = "INSERT INTO sites (name, url) VALUES (%s, %s)"
val = [
  ('Google', 'https://www.google.com'),
  ('Github', 'https://www.github.com'),
  ('Taobao', 'https://www.taobao.com'),
  ('stackoverflow', 'https://www.stackoverflow.com/')
]
 
mycursor.executemany(sql, val)

为了防止数据库查询发生 SQL 注入的攻击，我们可以使用 %s 占位符来转义查询的条件：
sql = "SELECT * FROM sites WHERE name = %s"
na = ("RUNOOB", )
mycursor.execute(sql, na)
```

```python
import pymysql#使用另一个连接库
 
# 打开数据库连接
db = pymysql.connect(host='localhost',
                     user='testuser',
                     password='test123',
                     database='TESTDB')
 
# 使用 cursor() 方法创建一个游标对象 cursor
cursor = db.cursor()
 
# 使用 execute()  方法执行 SQL 查询 
cursor.execute("SELECT VERSION()")
```

```python
from urllib.request import urlopen
myurl = urlopen("https://www.runoob.com/")
lines = myurl.readlines()
for line in lines:
    print(line)

print(myurl.read(300))#读取300行

print(myurl.read())#读取全部
print(myurl.readline())

f = open("text.txt","wb")#写入 文件
content = myurl.read()
f.write(content)
f.close()

#我们抓取网页一般需要对 headers（网页头信息）进行模拟，这时候需要使用到 urllib.request.Request 类：

class urllib.request.Request(url, data=None, headers={}, origin_req_host=None, unverifiable=False, method=None)


error：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：：
try:
    myURL2 = urllib.request.urlopen("https://www.runoob.com/no.html")
except urllib.error.HTTPError as e:
    if e.code == 404:
        print(404)   # 404
        
import urllib.request
import urllib.parse

url = 'https://www.runoob.com/try/py3/py3_urllib_test.php'
data = {'name':'RUNOOB','tag':"菜鸟教程"}
header = {
'User-Agent':'Mozilla/5.0 (X11; Fedora; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/58.0.3029.110 Safari/537.36'
}
data = urllib.parse.urlencode(data).encode('utf8')
request=urllib.request.Request(url,data,header)
reponse=urllib.request.urlopen(request).read()
fh = open("E:/Python/urllib/urllib_test_post_runoob.html","wb")
fh.write(reponse)
fh.close()
```

```python
User-agent: *
Disallow: /
Allow: /public/
User-agent 描述了搜索’爬虫的名称，这里将其设置为＊则代表该协议对任何爬取爬虫有效。
比如，我们可以设置：
User-agent: Baiduspider
这就代表我们设置的规则对百度爬虫是有效的。如果有多条User-agent 记录，则就会有多个爬虫
会受到爬取限制，但至少需要指定一条。
Disallow 指定了不允许抓取的目录，比如上例子中设置为／则代表不允许抓取所有页面。
Allow 一般和Disallow 一起使用，一般不会单独使用，用来排除某些限制。现在我们设置为
/public ／，则表示所有页面不允许抓取，但可以抓取public 目录。
```

## urllib.robotparser



# Python math 模块

Python **math** 模块提供了许多对浮点数的数学运算函数。

**math** 模块下的函数，返回值均为浮点数，除非另有明确说明。

如果你需要计算复数，请使用 **cmath** 模块中的同名函数。

要使用 math 函数必须先导入：

```python
import math
```

# Python requests 模块

Python 内置了 requests 模块，该模块主要用来发 送 HTTP 请求，requests 模块比 [urllib](https://www.runoob.com/python3/python-urllib.html) 模块更简洁。

```python
# 导入 requests 包
import requests

 
kw = {'s':'python 教程'}

# 设置请求头
headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.99 Safari/537.36"}
 
# params 接收一个字典或者字符串的查询参数，字典类型自动转换为url编码，不需要urlencode()
response = requests.get("https://www.runoob.com/", params = kw, headers = headers)

# 查看响应状态码
print (response.status_code)

# 查看响应头部字符编码
print (response.encoding)

# 查看完整url地址
print (response.url)

# 查看响应内容，response.text 返回的是Unicode格式的数据
print(response.text)
```

