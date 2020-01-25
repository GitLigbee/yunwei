1. 修改sshd配置文件
> vim /etc/ssh/sshd_config
```
#SyslogFacility AUTHPRIV
SyslogFacility local1
```
2. 修改rsyslog服务的配置文件来管理本地日志
> vim /etc/syslog.conf
```
local1.*       /var/log/sshd.log
```