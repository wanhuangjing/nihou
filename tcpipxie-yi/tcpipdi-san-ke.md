\#

### TCP/IP 协议族

#### TCP/IP层次

* Application: OSI模型中第5，6，7层
* Transport: OSI模型中的第4层
* Internet: OSI模型中的第三层
* Network Access: OSI模型中的第1，2，3层

##### 对于因特网来说，它所互联的网络是物理网络（物理层和数据链路层），然而这些物理网络内部的传输机制完全不一样，这种特性使得他们直接在数据链路层上进行通信是不可能的。因此，对于因特网来说，它采用一种专门的设备，也就是路由器，将这些不同实现不同通信方式的物理网络之间通过路由器进行互联

![](/assets/18-4-26-1.png)

##### 上图也是一种物理网络，只不过是点到点式的

#### 如何看待互联网

* 用户角度

  ##### 单一的虚拟网络

  ##### 无需了解网络的内部结构

* 互联网角度

  ##### 所有网络是平等的（这里的所有网络指的是这些互联设备所互联的不同类型的物理网络，平等是指即使这些网络的体系结构、传输机制不完全相同，对于这些互联设备而言，在传输时仍然要一视同仁）

  ##### 路由器每个接口连接的都是网络

##### ![](/assets/18-4-29-1.png)

##### 虽然从TCP/IP的协议模型来看，它包含了四个层次，也就是说它最下面一层是网络接入层，完成的是OSI参考模型的数据链路层和物理层的功能，但是在TCP/IP的协议族中，并没有包含网络接入层的协议标准。

##### 为什么还是列入TCP/IP协议的层次结构中：通信要完成的话，最终是要通过这些物理介质完成，而数据要传输到物理介质上面，当然离不开数据链路层和物理层，对于数据链路层来说，控制了这些通讯节点到底如何访问介质，如何获得这些介质的使用权，而物理层的功能当然是将相应的计算机中的信号这些二进制代码转换成为相应的传输介质上的传输信号发送出去

##### 物理网内部的传输标准，实际上不是TCp/IP所要解决的问题，因为从互联网的角度来看，所有的网络都是平等，因此对于TCP/IP协议来说，他解决的不是这些物理网内部的通信方式，而是这些物理网之间如何实现通信，所以对于这些物理网内部的通信机制，TCP/IP协议并不包含这些内容，它可以用在现有任何的任何一种物理网上，这也是TCP/IP所制定的一个目标，他希望在任何的环境下使用。

##### 网际层实际上为上面的传输服务提供了统一的访问不同物理网络的一个接口，而传输层又是为上面不同的网络应用提供了传输的通道，多种网络应用可以使用相同的传输通道，只要他们所需要的传输服务是一致的

##### socket：套接字，并不是tcp/ip中的一个层次，他是一个接口，来实现上下层之间的服务的提供和使用


