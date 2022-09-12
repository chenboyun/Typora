ens33:   /etc/sysconfig/network-scripts/ifcfg-ens33

systemctl restart network.service

service network restart

systemctl start network.service

```bash
systemctl stop firewalld
 systemctl disable firewalld
 查看状态
 systemctl status firewalld
```

解决NAT：

[(32条消息) Win11安装VMware16和Centos7并选择NAT模式(详细版)_花僧码农的博客-CSDN博客_win11安装vmware](https://blog.csdn.net/qq_44327755/article/details/125172219)

**systemctl disable firewalld.service**，开机禁止防火墙服务器
**systemctl enable firewalld.service**，开机启动防火墙服务器

强制关掉yum进程     rm -f /var/run/yum.pid