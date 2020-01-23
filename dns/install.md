### install

> instruction
域名解析服务，提供正向解析[域名->ip],反向解析[ip->域名]，其配置又称为A记录

### install step
1. 关闭防火墙
2. 配置yum源
3. 安装软件【bind】
```
> sudo yum -y install bind

> rpm -q bind ;确认是否成功安装
bind-9.11.4-9.P2.el7.x86_64

> rpm -ql bind ;查看配置文件
/etc/logrotate.d/named ;日志轮转文件
/etc/named ;配置文件主目录
/etc/named.conf ;主配置文件
/etc/named.rfc1912.zones ;子配置文件，定义域
/usr/sbin/named ;二进制文件
/usr/sbin/named-checkconf ;检查配置文件
/usr/sbin/named-checkzone ;检查区域文件
/var/log/named.log ;日志文件
/var/named ;数据文件主目录
/var/named/data
/var/named/dynamic
/var/named/named.ca ;根域服务器
/var/named/named.empty
/var/named/named.localhost ;正向解析区域文件模板
/var/named/named.loopback ;反向解析区域文件模板
/var/named/slaves ;从dns服务器下载文件的默认路径
```
4. 配置
> vim /etc/named.conf
```
options {
	listen-on port 53 { 127.0.0.1;any; }; //定义监听方式，any代表监听所有网卡
    ...
	allow-query     { localhost;any; }; // 允许任何人查询
    ...
};
```
> vim /etc/named.rfc1912.zones
```
;正向解析
zone "dnstest.com" IN {
        type master;
        file "dnstext.com.zone";
        allow-update { none; };
};
;反向解析
zone "1.168.192.in-addr.arpa" IN {
        type master;
        file "1.168.192.zone";
        allow-update { none; };
};
```
> cd /var/named ;在数据目录下配置新增的解析

> cp -p named.localhost dnstest.com.zone ;-p保持原组属

> vim dnstest.com.zone
```
$TTL 1D ;缓存时间1天
@       IN SOA  dnstest.com. rname.invalid. (
                                        0       ; serial
                                        1D      ; refresh
                                        1H      ; retry
                                        1W      ; expire
                                        3H )    ; minimum
        NS      serve.dnstest.com. ;NS代表nameserver,前两行必须指定dns服务的IP
serve   A       192.168.1.100
hello   A       192.168.1.100 ;解析hello.dnstest.com
```
> vim 1.168.192.zone
```
$TTL 1D
@	IN SOA	dnstest.com. rname.invalid. (
					0	; serial
					1D	; refresh
					1H	; retry
					1W	; expire
					3H )	; minimum
	NS	serve.dnstest.com.
100	PTR	hello.dnstest.com.
```
5. 语法检测
> named-checkconf /etc/named.conf

> named-checkconf /etc/named.rfc1912.zones

> named-checkzone dnstest.com.zone dnstest.com.zone

> named-checkzone 100.1.168.zone 100.1.168.zone
```
zone testdns.com.zone/IN: loaded serial 0
OK
```
6. 启动服务
> service named start

> netstat -nulp | grep named
```
udp        0      0 192.168.122.1:53        0.0.0.0:*                           20043/named
udp        0      0 192.168.1.100:53        0.0.0.0:*                           20043/named
udp        0      0 127.0.0.1:53            0.0.0.0:*                           20043/named
udp6       0      0 ::1:53                  :::*                                20043/named
```
7. 测试
```
1) dig 
dig @192.168.1.100 hello.dnstest.com ;正向解析
dig -x 192.168.1.100 @192.168.1.100 ;反向解析

2) nslookup
echo nameserver 192.168.1.100 >> /etc/resolv.conf
nslookup hello.dnstest.com

3)
host hello.dnstest.com
```
