> 将ftp服务的上传下载日志单独记录到`/var/log/ftp.log`

修改ftp服务的配置文件指定让rsyslog程序管理日志（定义设备载体）
> man 5 vsftpd.conf
```
syslog_enable
    If enabled, then any log output which would have gone to /var/log/vsftpd.log goes to the system log instead. Logging is done under the FTPD facility.

    Default: NO
```
> vim /etc/vsftpd/vsftpd.conf
```
syslog_enable=YES
```
> service vsftpd restart

> vim /etc/syslog.conf ;修改rsyslog服务的配置文件来管理本地日志
```
ftp.*       /var/log/ftp.log
```
> service rsyslog restart