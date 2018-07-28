# [ Ubuntu下使用UFW配置防火墙（简化iptables的操作）](https://www.cnblogs.com/EasonJim/p/6851241.html)

**UFW**全称为**Uncomplicated Firewall**，是**Ubuntu**系统上配置**iptables**防火墙的工具。**UFW**提供一个非常友好的命令用于创建基于**IPV4**，**IPV6**的防火墙规则。 但是，**UFW**是没有界面的，就是用命令的那一种，所以，操作起来就不是那么的方便，有人帮它写了个界面，名字就叫做“**Gufw**”。

由于**Ubuntu**下的**iptables**操作起来比较复杂，依赖关系比较多，所以使用**UFW**时可以简化很多操作。当然**Debian**同样适用。

无论是桌面版还是服务器版,**UFW**的命令行用法是一样的。



**一、安装UFW**

首先，用如下命令来检查下系统上是否已经安装了**UFW**。

```
$ sudo dpkg --get-selections | grep ufw
```

如还没有安装，可以使用**apt**命令来安装，如下所示：

```
$ sudo apt-get install ufw
```

在使用前，你应该检查下**UFW**是否已经在运行。用下面的命令来检查：

```
$ sudo ufw status
```

如果你发现状态是：**inactive**, 意思是没有被激活或不起作用。

**二、使用方法**

1、启用

```
sudo ufw enable
sudo ufw default deny 
#作用：开启了防火墙并随系统启动同时关闭所有外部对本机的访问（本机访问外部正常）。
```

2、关闭

```
sudo ufw disable
```

2、查看防火墙状态

```
sudo ufw status
```

3、开启/禁用相应端口或服务举例


```
sudo ufw allow 80 #允许外部访问80端口
sudo ufw delete allow 80 #禁止外部访问80 端口
sudo ufw allow from 192.168.1.1 #允许此IP访问所有的本机端口
sudo ufw deny smtp #禁止外部访问smtp服务，#以服务名代表端口，可以使用less /etc/services列出所有服务信息, 其中包括该服务使用了哪个端口和哪种协议
sudo ufw delete allow smtp #删除上面建立的某条规则，或者sudo ufw delete allow 80/tcp，如果出现无法删除，可以用序号：sudo ufw status numbered，然后通过序号删除sudo ufw delete 1
sudo ufw deny proto tcp from 10.0.0.0/8 to 192.168.0.1 port 22 #要拒绝所有的TCP流量从10.0.0.0/8到192.168.0.1地址的22端口

#可以允许所有RFC1918网络（局域网/无线局域网的）访问这个主机（/8,/16,/12是一种网络分级）：
sudo ufw allow from 10.0.0.0/8

sudo ufw allow from 172.16.0.0/12

sudo ufw allow from 192.168.0.0/16
```


4、重置所有规则

```
sudo ufw reset
```



