* 查询端口号80的tcp协议是否开启：`firewall-cmd --query-port=80/tcp`

* 永久开放80端口的tcp协议：`firewall-cmd --permanent --zone=public --add-port=80/tcp`

* 移除80端口的tcp协议： `firewall-cmd --permanent --zone=public --remove-port=80/tcp`

* 查看防火墙状态： `systemctl status firewalld`

* 启动\|关闭\|重新启动 防火墙： `systemctl [start|stop|restart] firewalld`

##### --zone: 作用域

##### --add-port=80/tcp: 添加端口，格式,端口/通讯协议

##### -permanent: 永久生效，没有此参数重启后失效



FirewallD 使用服务（service） 和区域（zone）来代替 iptables 的规则（rule）和链（chain）。

默认情况下，有以下的区域（zone）可用：

1. **drop**
   – 丢弃所有传入的网络数据包并且无回应，只有传出网络连接可用。
2. **block**
   — 拒绝所有传入网络数据包并回应一条主机禁止的 ICMP 消息，只有传出网络连接可用。
3. **public**
   — 只接受被选择的传入网络连接，用于公共区域。
4. **external**
   — 用于启用了地址伪装的外部网络，只接受选定的传入网络连接。
5. **dmz**
   — DMZ 隔离区，外部受限地访问内部网络，只接受选定的传入网络连接。
6. **work**
   — 对于处在你工作区域内的计算机，只接受被选择的传入网络连接。
7. **home**
   — 对于处在你家庭区域内的计算机，只接受被选择的传入网络连接。
8. **internal**
   — 对于处在你内部网络的计算机，只接受被选择的传入网络连接。
9. **trusted**
   — 所有网络连接都接受。

要列出所有可用的区域，运行：

```
# firewall-cmd --get-zones
work drop internal external trusted home dmz public block

```

列出默认的区域 ：

```
# firewall-cmd --get-default-zone
public

```

改变默认的区域 ：

```
# firewall-cmd --set-default-zone=dmz
# firewall-cmd --get-default-zone
dmz

```

**FirewallD 服务**

FirewallD 服务使用 XML 配置文件，记录了 firewalld 服务信息。

列出所有可用的服务：

```
# firewall-cmd --get-services
amanda-client amanda-k5-client bacula bacula-client ceph ceph-mon dhcp dhcpv6 dhcpv6-client dns docker-registry dropbox-lansync freeipa-ldap freeipa-ldaps freeipa-replication ftp high-availability http https imap imaps ipp ipp-client ipsec iscsi-target kadmin kerberos kpasswd ldap ldaps libvirt libvirt-tls mdns mosh mountd ms-wbt mysql nfs ntp openvpn pmcd pmproxy pmwebapi pmwebapis pop3 pop3s postgresql privoxy proxy-dhcp ptp pulseaudio puppetmaster radius rpc-bind rsyncd samba samba-client sane smtp smtps snmp snmptrap squid ssh synergy syslog syslog-tls telnet tftp tftp-client tinc tor-socks transmission-client vdsm vnc-server wbem-https xmpp-bosh xmpp-client xmpp-local xmpp-server

```

XML 配置文件存储在 /usr/lib/firewalld/services/ 和 /etc/firewalld/services/ 目录下。

**用 FirewallD 配置你的防火墙**

作为一个例子，假设你正在运行一个 web 服务器，SSH 服务端口为 7022 ，以及邮件服务，你可以利用 FirewallD 这样配置你的服务器:

首先设置默认区为 dmz。

```
# firewall-cmd --set-default-zone=dmz
# firewall-cmd --get-default-zone
dmz

```

为 dmz 区添加持久性的 HTTP 和 HTTPS 规则：

```
# firewall-cmd --zone=dmz --add-service=http --permanent
# firewall-cmd --zone=dmz --add-service=https --permanent

```

开启端口 25 \(SMTP\) 和端口 465 \(SMTPS\) ：

```
firewall-cmd --zone=dmz --add-service=smtp --permanent
firewall-cmd --zone=dmz --add-service=smtps --permanent

```

开启 IMAP、IMAPS、POP3 和 POP3S 端口：

```
firewall-cmd --zone=dmz --add-service=imap --permanent
firewall-cmd --zone=dmz --add-service=imaps --permanent
firewall-cmd --zone=dmz --add-service=pop3 --permanent
firewall-cmd --zone=dmz --add-service=pop3s --permanent

```

因为将 SSH 端口改到了 7022，所以要移除 ssh 服务（端口 22），开启端口 7022：

```
firewall-cmd --remove-service=ssh --permanent
firewall-cmd --add-port=7022/tcp --permanent

```

要应用这些更改，我们需要重新加载防火墙：

```
firewall-cmd --reload

```

最后可以列出这些规则：

```
# firewall-cmd –list-all
dmz
target: default
icmp-block-inversion: no
interfaces:
sources:
services: http https imap imaps pop3 pop3s smtp smtps
ports: 7022/tcp
protocols:
masquerade: no
forward-ports:
sourceports:
icmp-blocks:
rich rules:
```



