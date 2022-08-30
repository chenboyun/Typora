嗯G银克斯

正向代理和反向代理：

**正向代理，其实是"代理服务器"代理了"客户端"，去和"目标服务器"进行交互。**

如我访问外网

通过正向代理服务器访问目标服务器，目标服务器是不知道真正的客户端是谁的，甚至不知道访问自己的是一个代理

上网者也可以通过这种方法隐藏自己的IP，免受攻击。

反向代理：(我们要访问的被代理了)还有一种情况，就是我们以为我们接触的是房东，其实有时候也有可能并非房主本人，有可能是他的亲戚、朋友，甚至是二房东。但是我们并不知道和我们沟通的并不是真正的房东。这种帮助真正的房主租房的二房东其实就是反向代理服务器。这个过程就是反向代理。**所以，反向代理，其实是"代理服务器"代理了"目标服务器"，去和"客户端"进行交互。**

通过反向代理服务器访问目标服务器时，客户端是不知道真正的目标服务器是谁的，甚至不知道自己访问的是一个代理。使用反向代理，可以对客户端隐藏服务器的IP地址。

即，租客并不房东知道的真实身份。

**负载均衡**

反向代理服务器可以做负载均衡，根据所有真实服务器的负载情况，**将客户端请求分发到不同的真实服务器上。**

即，二房东发现房主本人很忙，于是找到房主的妻子帮忙处理租房事宜。

**提高访问速度**

反向代理服务器可以对**于静态内容及短时间内有大量访问请求的动态内容提供缓存服务，提高访问速度。**

即，二房东同样有房屋信息和钥匙。

**提供安全保障**

反向代理服务器可以作为应用层防火墙，为网站提供对基于Web的攻击行为（例如DoS/DDoS）的防护，更容易排查恶意软件等。还可以为后端服务器统一提供加密和SSL加速（如SSL终端代理），提供HTTP访问认证等。
1、**正向代理其实是客户端的代理**，帮助客户端访问其无法访问的服务器资源。**反向代理则是服务器的代理**，帮助服务器做负载均衡，安全防护等。

2、**正向代理一般是客户端架设的**，比如在自己的机器上安装一个代理软件。而**反向代理一般是服务器架设的**，比如在自己的机器集群中部署一个反向代理服务器。

3、**正向代理中，服务器不知道真正的客户端到底是谁**，以为访问自己的就是真实的客户端。而在**反向代理中，客户端不知道真正的服务器是谁**，以为自己访问的就是真实的服务器。

4、正向代理和反向代理的作用和目的不同。**正向代理主要是用来解决访问限制问题。而反向代理则是提供负载均衡、安全防护等作用。二者均能提高访问速度。**

## 尚硅谷课程

![image-20220830094611897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830094611897.png)

我们把这两个当成一个服务器来使用![image-20220830094654524](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830094654524.png)

对外暴露的是9001  真是访问的是8001

![image-20220830095743752](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830095743752.png)

动静分离

nigix.config  里面的默认端口号是80![image-20220830125935936](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830125935936.png)

不同路径   不同服务器![image-20220830140252618](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830140252618.png)

![image-20220830145108316](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830145108316.png)

三种分配方式：ip hash可以解决session问题

动静分离：静态请求和动态请求分离开来，而不是仅仅的资源的动静![image-20220830150632415](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830150632415.png)

![image-20220830151818714](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830151818714.png)





# 命令

```bash
cd /usr/local/nginx/sbin  
./nginx -s stop   停止

/////////////////////////
make && make install
ps -ef | grep nginx      //查看pid
firewall-cmd --list-all   //查看开放的端口号
firewall-cmd --add-service=http –permanent  //设置开放的端口号
firewall-cmd --add-port=80/tcp --permanent
firewall-cmd –reload   //重启防火墙


:set number    //行数
:set nonumber
```

# 常见错误

nginx: [emerg] unknown directive "　　proxy_pass" in /etc/nginx/conf.d/netcore.conf:10

最终排查原因是我在配置中使用Tab键代替了空格所致，所以当我把配置文件中的Tab替换成空格后一切都正常了。

是proxy_pass   中间不是空格。是下划线![image-20220830140032690](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220830140032690.png)

