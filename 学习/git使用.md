找开源项目的一些途径
• https://github.com/trending/
• https://github.com/521xueweihan/HelloGitHub
• https://github.com/ruanyf/weekly
• https://www.zhihu.com/column/mm-fe

特殊的查找资源小技巧-常用前缀后缀 
• 找百科大全 awesome xxx          最全的，还有很多人贡献   如 awesome vue
• 找例子 xxx sample					 可以通过别人的例子来学习代码
• 找空项目架子 xxx starter / xxx boilerplate     比如mybatis - springboot-strat
• 找教程  xxx tutorial

clone会有一个.git文件，而下载压缩包后解压，没有.git文件，说明只是一个文件，而不是一个仓库

克隆仓库：git clone <git地址>
初始化仓库：git init 

添加文件到暂存区：git add -A
把暂存区的文件提交到仓库：git commit -m "提交信息"
查看提交的历史记录：git log --stat

通常我们使用 **-s** 参数来获得简短的输出结果：

```
$ git status -s
```

工作区回滚：git checkout <filename>
撤销最后一次提交：git reset HEAD^1

以当前分支为基础新建分支：git checkout -b <branchname>
列举所有的分支：git branch
单纯地切换到某个分支：git checkout <branchname>
删掉特定的分支：git branch -D <branchname>
合并分支：git merge <branchname>

推送当前分支最新的提交到远程：git push  我们之前的修改和仓库都在本地仓库
拉取远程分支最新的提交到本地：git pull

![image-20220813072037459](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220813072037459.png)

```cmd
$ git reset HEAD^            # 回退所有内容到上一个版本  
$ git reset HEAD^ hello.php  # 回退 hello.php 文件的版本到上一个版本  
$ git  reset  052e           # 回退到指定版本
git reset --soft HEAD
$ git reset --soft HEAD~3   # 回退上上上一个版本 
```

- 

- ```
  $ git log --oneline   //我们可以用 --oneline 选项来查看历史记录的简洁的版本。
  
  $ git log --reverse --oneline //你也可以用 --reverse 参数来逆向显示所有日志。
  
  $ git log --author=Linus --oneline -5  //如果只想查找指定用户的提交日志可以使用命令：git log --author , 例如，比方说我们要找 Git 源码中 Linus 提交的部分：
  
  git blame <file>   //如果要查看指定文件的修改记录可以使用 git blame 命令，
  ```

- 

- ```java
  git remote -v   //显示所有远程仓库：    origin 为远程地址的别名。
  
  git remote show [remote]   //  显示某个远程仓库的信息
  ```

# 问题解决

**取消代理**  

git config --global --unset http.proxy

git config --global --unset https.proxy

本地和远程仓库两者代码文件不同步，因此需要先pull，进行合并然后再进行push

### 解决方法：



```bash
git pull --rebase origin master   $1、先使用pull命令：
git push -u origin master          $2、再使用push命令：
```







# 学习笔记

![image-20220829192640431](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829192640431.png)’

林大神    	发明  Linux  git

![image-20220829193354627](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829193354627.png)

![image-20220829193602521](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829193602521.png)

git  init  让git获取管理权

没有办法表达出修改一行，只能说删除一行，之后增加一行![image-20220829195328030](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829195328030.png)

指向了这个版本![image-20220829195445123](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829195445123.png)



![image-20220829200538552](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829200538552.png)

![image-20220829200751176](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829200751176.png)

![image-20220829200847144](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829200847144.png)

![image-20220829201732346](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829201732346.png)

打开出现问题的文件![image-20220829202437877](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829202437877.png)

当前分支  冲突分支   自己修改成能用的  之后![image-20220829202607628](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829202607628.png)

合并分支只会修改合并的分支，不会修改另一个分支

![image-20220829203845021](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829203845021.png)

跨团队协作![image-20220829204117921](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829204117921.png)

fork  叉子   把远程库拿过来   

git  代码都是在本地库里面写的，所以叫分布式版本控制

pull request  拉取请求

想要同步本地库和远程库，要拉取代码

![image-20220829210215401](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829210215401.png)

origin 是默认的别名

![image-20220829210402862](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829210402862.png)

直接推送代码，需要加入到这个团队里面，否则没有权限

加入团队的认证（一个链接）![image-20220829210604872](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829210604872.png)

![image-20220829212036653](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829212036653.png)

**在家目录下新建了一个   git.ignore     c:用户:adm:git.ignore**

前往下方的网址，可以自动生成.[gitignore](https://so.csdn.net/so/search?q=gitignore&spm=1001.2101.3001.7020)文件

https://www.toptal.com/developers/gitignore

idea里面修改git.ignore![image-20220829213011867](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213011867.png)

![image-20220829213019635](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213019635.png)

![image-20220829213028627](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213028627.png)

定位git的应用程序

![image-20220829213142152](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213142152.png)

![image-20220829213159644](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213159644.png)

之后选中项目，直到出现![image-20220829213224243](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213224243.png)

![image-20220829213354422](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213354422.png)

![image-20220829213441037](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213441037.png)

![image-20220829213643701](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213643701.png)

log里面可以看到三个版本![image-20220829213659482](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213659482.png)

切换版本![image-20220829213735202](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213735202.png)

创建分支![image-20220829213835276](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213835276.png)

右下角可以看到是哪个分支![image-20220829213923494](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829213923494.png)

合并分支![image-20220829214111946](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829214111946.png)



## 命令

```livescript
git rm --cached hello.txt
git commit -m ""     //-m  是提交信息的意思，不写，之后也要写
$ git reflog   //查看版本日志信息
 git log     //详细版
git reset --hard  版本号//版本号在  git relog 时显示在最前面
git branch   branchname   创建分支
git branch -v   查看分支
git checkout branchname   切换分支
git merge  branchname  指定分支合并到当前分支上。   //合并 融合
git remote -v     查看别名
git remote add Typora https://github.com/chenboyun/Typora.git  添加别名 
git push Typora 分支名    //推送
git pull Typora main  //拉取代码
git clone https.................  //克隆，不需要登陆，因为是公共的

```

寻找git.config    git config --list --show-origin
