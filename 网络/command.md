- 显示所有网卡
ip a

- 只显示激活网卡
ifconfig
ifconfig -a // 显示所有

- 查看路由表信息,可查看默认网关信息
route -n

- 修改主机名
```
vim /etc/sysconfig/network
--------
HOSTNAME=MyName
--------
// OR
hostname=MyName
```

- 关闭防火墙
service iptables stop // 临时关闭
chkconfig iptables off // 永久关闭
chkconfig --list | grep iptables

- linux 安全级别 
getenforce
setenforce 0
``` 永久关闭 
vim /etc/selinux/config
------------------------
SELINUX=disabled ; 严格：enforcing
------------------------
```