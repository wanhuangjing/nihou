* 查询端口号80的tcp协议是否开启：`firewall-cmd --query-port=80/tcp`

* 永久开放80端口的tcp协议：`firewall-cmd --permanent --zone=public --add-port=80/tcp`

* 移除80端口的tcp协议： `firewall-cmd --permanent --zone=public --remove-port=80/tcp`

* 查看防火墙状态： `systemctl status firewalld`
* 启动|关闭|重新启动 防火墙： `systemctl [start|stop|restart] firewalld`

##### --zone: 作用域
##### --add-port=80/tcp: 添加端口，格式,端口/通讯协议
##### -permanent: 永久生效，没有此参数重启后失效



