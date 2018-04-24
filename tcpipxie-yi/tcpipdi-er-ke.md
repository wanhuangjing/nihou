#### OSI参考模型

* ISO标准：Open System Interconnection，开放系统互连， Reference Model，参考模型
* 目的：是两个不同的系统能够通信，而不需要改变底层的硬件或软件逻辑
  ** ISO是一个组织，OSI是一个模型**
  ** OSI不是协议，是网络体系结构的**_**概念模型**_** **

#### OSI层次体系结构

* Application  应用层
* Presentation 表现层
* Session 会话层
* Transport  传输层
* Network 网络层
* Data Link 数据链路层
* Physical 物理层

##### 应用支持层（软件）：Application,Presentation,Session

##### 网络支持层（软/硬件）： Network,Data Link, Physical

#### 对等层通信

![](/assets/18-4-22-4.png)

#### 服务：下层对上层提供的一些操作，一些功能，下层被称为服务提供者，上层被称为服务使用者

##### 服务只能在一个系统内，数据链路层只能向自己的网络层提供服务，而不能向下提供服务，同时也不能向其他节点的网络层提供服务

##### 服务只能在相邻层之间，不能跨层次，比如说，物理层直接给网络层提供服务

#### 接口：层和层之间有一个接口，这个接口为了实现层和层之间服务的使用，在每一层之间都有接口，服务的提供和使用都是通过这个接口来实现的

![](/assets/18-2-22-5.png)

#### 对等层（Peer Layer）：不同系统上的同一层，比如设备A与设备B之间的会话层

![](/assets/18-2-22-6.png)

#### 对等进程/对等实体（Peer Entity）：对等层上的实体，因为大家都在同一层次上面，完成同一功能，只是位于不同的系统

![](/assets/18-2-22-7.png)

#### 对等层协议（Peer-to-Peer Protocol）：对等实体之间的通信规则

![](/assets/18-2-22-8.png)

#### 对等层与对等实体

![](/assets/18-2-22-9.png)

##### 因为要完成不同的功能，所以有不同的实体，而这些实体为了完成这些不同的功能，相应的要使用不同的协议来实现，不同的对等实体的之间通信，要使用的不同的协议，因此每一层可以存在多个协议

##### 每一层可以同时存在多个实体

##### 每一层可以存在多个协议

** 存在通信关系的对等层实体才是对等层实体  **  
** 协议时对等实体间的通信规则 **

![](/assets/18-4-23-1.png)
##### 数据在进行通信的时候，上层将数据递交给下层，下层收到上层的数据之后，在收到的数据前面添加本层的一些控制信息
##### PDU（Protocol Data Unit 协议数据单元）:对等实体之间通讯时所传输的信息的内容，每一层都有自己的PDU

##### 帧（Frame）:数据链路层的PDU

##### 分组（Packet）：网络层的PDU

##### 数据段（Segment）：传输层的PDU

##### 数据（Data）：5，6，7层的PDU

![](/assets/18-4-23-2.png)

* Application: Network processes to applications
* Presentation:Data representation
* Session:Inter-host communication
* Transport:End-to-end connections
* Network:Addressing and best path
* Data Link:Access to media
* Physical:Binary transmission



