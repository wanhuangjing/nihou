本文章来给各位同学介绍一下关于Centos6修改sysctl.conf报错解决方法,如果你碰到此类问题不防进入参考一下。
这几天一直在折腾VPS优化，openvz构架的，在做linux内核优化的时候，执行/sbin/sysctl -p老报错：
error: "net.bridge.bridge-nf-call-ip6tables" is an unknown key
error: "net.bridge.bridge-nf-call-iptables" is an unknown key
error: "net.bridge.bridge-nf-call-arptables" is an unknown key
error: permission denied on key 'net.ipv4.tcp_max_syn_backlog'
error: permission denied on key 'net.core.netdev_max_backlog'
error: permission denied on key 'net.core.wmem_default'
error: permission denied on key 'net.core.rmem_default'
error: permission denied on key 'net.core.rmem_max'
error: permission denied on key 'net.core.wmem_max'
error: permission denied on key 'net.ipv4.tcp_timestamps'
error: permission denied on key 'net.ipv4.tcp_synack_retries'
error: permission denied on key 'net.ipv4.tcp_syn_retries'
error: permission denied on key 'net.ipv4.tcp_tw_recycle'
error: permission denied on key 'net.ipv4.tcp_tw_reuse'
error: permission denied on key 'net.ipv4.tcp_mem'
error: permission denied on key 'net.ipv4.tcp_max_orphans'
error: permission denied on key 'net.ipv4.ip_local_port_range'
然后就去找资料解决，网络上说前三个错误执行：
帮助12 modprobe bridge lsmod|grep bridge
命令即可，但在执行第一个命令的时候又遇到新错误了~~~
FATAL: Module bridge not found.
咋办，又得去找资料，一开始用百度，找了好久，没一个解决的，后来果断用谷歌啊，接着，你懂的，找到了解决方案，但TM全是英文（也是我发这篇博文的原因），还好我有chrome~碰巧的是顺带找到了后面那七八个错误的解决方案，大快人心啊！
原来这些问题都是因为openvz模版的问题（谷歌翻译是这样说的），要进行修复操作， 修复也很简单，总共四个命令~
修复modprobe的：
  代码如下       复制代码
rm -f /sbin/modprobe
ln -s /bin/true /sbin/modprobe
修复sysctl的：
  代码如下       复制代码
rm -f /sbin/sysctl
ln -s /bin/true /sbin/sysctl
按命令来看就是重建这两个模块的软连接，不过，，，其实我也不是特别清楚，嘿嘿~
执行完这四个命令后，你再试试/sbin/sysctl -p，果断没报错了~
