> dig 查看DNS解析过程
```
dig +trace www.baidu.com ;追踪dns解析过程
dig @server www.baidu.com ;正向解析查询
dig -x 192.168.1.100 @server ;反向解析
```

> nslookup 查看域名解析IP
`nslookup www.baidu.com`
`nslookup 127.0.0.1`

> host
```
host -a www.baidu.com //列出该主机详细的各项主机名设置数据。
host www.baidu.com // 列出www.baidu.com的IP地址。
host www.baidu.com DNS服务器的IP // 使用其他DNS服务器IP列出www.baidu.com的IP地址。
```