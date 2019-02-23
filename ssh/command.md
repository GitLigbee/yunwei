- 查看可执行文件安装包
which ssh
rqm -qf /yourBinPath/ssh
---------------------------------
openssh-clients-{version}
---------------------------------
- 查看安装包安装的可执行程序
rqm -ql openssh-clients

- 网络信息
netstat -tlnp | grep 22 ;t:tcp, l:listen, n:主机名转IP地址, p:程序
netstat -npt | grep 22
ss -nltp | grep 22
lsof -i:22

- 开机启动
vim /etc/rc.local