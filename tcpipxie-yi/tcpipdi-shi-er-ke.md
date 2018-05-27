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

##### 网络地址（Net address）：特定 Net id，全0Subnet id + 全0Host id，全1Host id->网络广播地址
##### 子网地址(Subnet address)：特定Net id + 特定 Subnet id + 全0Host id，全1Host id->子网广播地址
##### 主机地址（Host address）：特定Net id + 特定 Subnet id + 特定 Host id
