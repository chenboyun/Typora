Ctrl+Alt+F1--F6  打开终端控制台  F1是回去

super+ 空格   切换输入法

![image-20220528195023750](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220528195023750.png)

：u   撤回

dd   删除行

yy    p   复制粘贴

y$复制当前行开始到结束

y^复制当前行开始到光标

w   表示单词可以跳转单词，

yw 复制单词

dw 删除单词

x   剪切

X往后删除

r  更改当前光标位置

R更改前面的

shift   + ^   移动到行头，

shift  + $   移动到行尾

**e   跳到下一个词的词尾**

**b   上一个词的词头**

**shift +  h （可视范围）  或   gg（全文档）   移动到的当前的开头**

**shift +g   最后一行行尾    L 可视范围的行尾**

num+G  跳转到特定行

显示行号：： set nu     不显示： ：set nonu

![image-20220609213608713](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220609213608713.png)

 1Class.forName("com.mysql.cj.jdbc.Driver");2conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/user","root","123456");3String sql = "select * from user_loin where loginName = ? and loginPwd = ?";//框架，占位符4ps = conn.prepareStatement(sql);//编译5ps.setString(1,loginName);6ps.setString(2,loginPwd);7rs = ps.executeQuery();java

/   查找     n  下一个   shift+n  上一个

：noh    取消高亮

：s/boot/booooooooot   替换

：%s/babab/aaaaaa/g    全篇替换

ipconfig  而Linux中是  ifconfig

ctrl+shift+v   是粘贴

修改网络配置：vim /etc/sysconfig/network-scripts/ifcfg-ens33

dhcp: 动态分配IP

重启网络配置：service network restart

更改主机名：  host name    vim  /etc/hostname   hostnamectl set-hostname cby666 

hosts  文件：一个主机名和IP的通讯录

ssh root@cby100                     ESC是退出

PID   进程ID

系统服务  一开始到关机的服务

win+D键，就能马上返回到电脑桌面

alt+tab   切换窗口

d开头的，守护进程

![image-20220610203623788](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220610203623788.png)

setup   设置窗口   空格是是否选中

![image-20220610205942005](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220610205942005.png)

systemctl get-default   查看运行级别

init 3    init 5    切换运行级别

{

firewalld  防火墙

}

chkconfig network off     chkconfig network on     chkconfig -- list chkconfig -- level 3 network off

shutdown     shutdown   -c    shutdown  now   shutdown 3  (单位是分钟)

![image-20220610223453473](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220610223453473.png)

不断电就是说，内存的东西还是保持的

ls -l /bin/ grep sh   筛选  sh 的和详细信息，用一行显示

man   manual  ![image-20220610234511377](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220610234511377.png)

命令+   --help //要是外部命令

clear    reset  清空	/重新初始化

cd - 上一次的路径   cd   返回自己的主文件夹目录

带   .   的都是隐藏文件    

ls -al

mkdir -p   (顺便创建父目录)   mkdir a a/b a/b/c

rmdir -p a/b/c   如果删完子文件夹，父文件夹为空的话也删除

touch  创建文件    CP   复制文件

\   反斜杠代表Linux里面的原生命令

rm    删除	![image-20220611145919476](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220611145919476.png)

rm -rf /*    删库跑路     删除本目录下的所有内容  rm -f ./*

移动文件 或目录：   mn    abab      baba

cat    查看文件   -n   显示行号

more   比cat  更好用    空格翻页

less   和more  类似，但是是分页加载的

echo   -e  支持反斜杠

">"是重定向符号  是覆盖的    ">>"是追加的   可以和Echo结合  echo  abab >> info

head -n 100 info

tail -f   追更新   适合看日志文件   Ctrl s 是暂停   ctrl q 是继续 Ctrl c 是退出

ln  软链接

rm  软连接  是删除软连接    rm 软连接/   当成目录来看的了，会删除目录

显示日期：date +%Y m d H: M: S

useradd lty     passwd lty   

useradd -g(放进一个组)  datebase xyq

su  :  switch user   切换用户    可以退出这种会话  exit

查看自己是那个用户：   who am i （最原始会话）  whoami 目前是谁

vim /etc/sudoers   更改root =ALL(ALL) ALL    %well   组前面有%

  etc   group    groupadd   添加组   usermod -g xian xyq  将用户添加到组

id xyq    查看ID   

组的重命名    groupmod -n(表示重命名)   xianxian   xian      

删除组：    groupdel      

chmod    改变文件的属性  （改变访问权限）[{ugoa}{+-=}{rwx}]

或者    chmod 777 文件名  

递归授权    chmod -R 777 hhhh/

更改所属主和组：chown/chgrp  root 文件名

给该文件夹权限才可以操控他的文件？

find  查找    find /root -size +1M  ---locate   更快，因为是在数据库中查找的

更新数据库？     updatedb 

查找文件内容：   grep -n(显示行号) boot 文件

管道符号  '|'    ls | grep .cfg

wc   word count   单词词频的统计

压缩  解压缩：   gzip    得到.gz文件    使用gunzip解压缩

zip   unzip 更好用   -r压缩目录    -d<目录>指定解压位置

zip -r myzip.zip /root          unzip -d /root/tem myzip.zip

tar   只打包，不压缩![image-20220611223050807](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220611223050807.png)



du   查看磁盘占用空间

df   查看可用磁盘

free  使用空间

lsblk  块设备存储情况

ps   查看进程   只显示用户的   ps  -ef    ps  aux   pstree  -p(显示PID)  -u(显示所属用户)-f可以看父子关系

top   切换排序    shift+p (cpu)   shift+m(内存)

查看端口占用     netstat![image-20220612152049142](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220612152049142.png)

crontab    定时任务![image-20220612152804804](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220612152804804.png)

安装包管理   rpm  -qa  |grep firefox    rpm -qi(详细信息) firefox

-e   卸载    -nodeps   不考虑依赖    rpm  -e  --nodeps firefox

安装   rpm -ivh/安装 详细信息 进度条  软件包全名

bash   后面加目录   ./abab      .  和 source  是不起用子shell的

提升为全局变量，export my_var   子shell的更改，父shell无效

echo  "$a      a= $  ((1+9))"    a=$[2+29]

readonly b = 5          unset a

''单引号认得出来

