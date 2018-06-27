#### 子网构成方法
##### 定长子网划分（Fix length subnetting）
* 共享同一IP网络前缀的子网大小相同
* 划分依据：子网数量与子网内主机数量折中
* 特点：划分简单，地址分配较浪费，因为这时候它只能考虑子网数量或者是子网内主机数量之中的任何一个因素，而不可能两者兼顾

###### 变长子网划分（Variable length subnetting）
* 共享同一IP网络前缀的子网大小不同
* 划分依据： 子网内的主机数量
* 特点：灵活、高效利用地址空间
* 变长子网掩码（Variable-Length Subnet Mask）

#### 5.4 使用变长子网划分
![](/assets/18-6-3-1.png)
##### 每个物理网地址数量
* 本子网内主机术+本子网内路由器接口数+2
* Net 1 = 25+3(路由器接口地址)+2 = 30
* Net 2 = 3+3+2 = 8
* Net 3 = 50+1+2=53
* Net 4 = 40+1+2=43
* Net 5 = 60+1+2=63

##### 定长划分
* Mask = 255.255.255.192
* 每个IP子网的实际IP数量： 64
* IP地址总空间：5 * 64 = 32

##### 变长划分
* Net 1 Mask = /27
* Net 2 Mask = /29
* Net 3 Mask = /26
* Net 4 Mask = /26
* Net 5 Mask = /26
IP地址总空间： 32+8+64+64+64 = 232