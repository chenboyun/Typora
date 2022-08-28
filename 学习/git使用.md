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

