#### 掩码（Mask）

##### 子网掩码：Net id + Subnet id

##### 默认掩码：Net id

##### 子网中的特殊地址

![](/assets/18-5-27-1.png)

##### Host id绝对不能全0或者全1，但是对于Subnet id来说分两种情况，一种理论上不能全0或者全1，而第二种情况在实际运用当中，只要 Net id + Subnet id它们的总和不是全0或者全1就足够了

#### 术语

* 网络号（Net id）：IP地址的一个组成部分
* 网络地址（Net address）： 一个IP地址

* 子网号（Subnet id）：IP地址的一个组成部分

* 子网地址（Subnet address）：一个IP地址

* 主机号（Host id）：IP地址的一个组成部分

* 主机地址（Host address）：一个IP地址

##### 网络地址（Net address）：特定 Net id，全0Subnet id + 全0Host id，全1Host id-&gt;网络广播地址

##### 子网地址\(Subnet address\)：特定Net id + 特定 Subnet id + 全0Host id，全1Host id-&gt;子网广播地址

##### 主机地址（Host address）：特定Net id + 特定 Subnet id + 特定 Host id

#### 连续掩码和不连续掩码

##### 不连续掩码

##### 11111101 11101110 11110111 01111110

##### 0，1混杂在一起，是网络构成和路由选择变得复杂--不实用

##### 推荐使用连续掩码

##### 11111111 11111111 11111111 11000000

#### 掩码表示

##### 点分十进制表示

##### 255.255.255.192,Netid + Subnetid = 26bits，Hostid = 6bits

##### 位数表示

##### /26

#### 掩码运算--位与运算

* Net address = IP address & Mask
* Host address = IP address & Mask\(取反\)
* Address range = {Net address,Net address+Mask(取反)}

##### IP address = 200.6.12.55， Mask = 255.255.248.0
##### Net address = 200.6.12.55 & 255.255.248.0 = 200.6.8.0
![](/assets/18-5-27-2.png)
##### Host address = 200.6.12.55 & 0.0.7.255 = 0.0.4.55
![](/asset2/18/5/27-3.png)
##### 200.6.15.255 = 200.6.8.0 + 0.0.7.255
##### Address rang = {200.6.8.0,200.6.15.255} 2048个网络地址，2046个主机地址

##### 网络和子网表示








