#### centos防火墙

> 查看防火墙状态
```
systemctl status firewalld
firewall-cmd --state
```
> 操作防火墙服务
```
; 开启
service firewalld start
; 重启
service firewalld restart
; 关闭
service firewalld stop
```
> 查看防火墙规则
```
firewall-cmd --list-all 
firewall-cmd --zone=public --list-ports // 查看所有打开的端口
```
> 操作端口
```
; 查询端口是否开放
firewall-cmd --query-port=8080/tcp
; 开放80端口
firewall-cmd --permanent --add-port=80/tcp
;开启多个端口
firewall-cmd --permanent --zone=public --add-port=8080-8083/tcp

; 移除端口
firewall-cmd --permanent --remove-port=8080/tcp

; 针对某个 IP开放端口
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.142.166" port protocol="tcp" port="6379" accept"
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.0.233" accept"

; 针对一个ip段访问
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.0.0/16" accept"
firewall-cmd --permanent --add-rich-rule="rule family="ipv4" source address="192.168.1.0/24" port protocol="tcp" port="9200" accept"

;重启防火墙(修改配置后要重启防火墙)
firewall-cmd --reload

; 参数解释
1、firwall-cmd：是Linux提供的操作firewall的一个工具；
2、--permanent：表示设置为持久；
3、--add-port：标识添加的端口；
```