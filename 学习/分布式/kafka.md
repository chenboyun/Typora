卡夫卡

对硬盘顺序读写，甚至比对内存的读写还快，不是随机读写

点对点；发布定位

![image-20220829085148239](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829085148239.png![image-20220829085250029](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829085250029.png)

分区![image-20220829090215726](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220829090215726.png)

# 尚硅谷

想把一个数据库的表都放到一个分区里面可以考虑用表名作为键（key的哈希&分区数）

每次拉取，每个分区都要准备一个数据
