yum install vsftpd

;确认是否安装
rpm -q vsftpd
yum list installed | grep vsftpd

;查看安装列表
rpm -ql vsftpd
----
/etc/vsftpd/vsftpd.conf
/usr/sbin/vsftpd
/usr/share/man/man5/vsftpd.conf.5.gz
/usr/share/man/man8/vsftpd.8.gz
/var/ftp
/var/ftp/pub
----