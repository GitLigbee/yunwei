- 查看光盘
lsblk

- 挂载
mount -o ro /dev/src0 /mnt/

- 存储信息
df -h

>>>
#### rpm
- 安装
rpm -ivh xxx

- 卸载
rpm -e xxx

- 升级，如果已安装老版本，则升级；如果没安装，则直接安装
rpm -Uvh

- 升级，如果已安装老版本，则升级；如果没安装，则不安
rpm -Fvh

- 强制安装
rpm -ivh --force

-- 忽略依赖关系
rpm --nodeps

-- 查看软件包文件列表
rpm -ql
rqm -ql xxx
rpm -qa ; 查看已安装的所有rpm包
rpm -qd ; 查看软件的文档列表
rpm -qi ; 查看软件的详细信息
rpm -qf filename ; 查看文件来自哪个rpm包
rpm -qc xxx ; 查看配置文件目录
------------------------
/etc    文件配置/启动脚本 /etc/rc.d/init.d/xxxx
/usr/sbin   二进制命令
/usr/share/doc  文档说明
/usr/share/man
/var    数据目录
-------------------------

-- 导入公钥用于检查rpm文件的签名
rpm --import /yourPathKeyFile/...

-- 检查rpm包签名
rpm --checksig xxx.rpm

<<<

- 修改man配置
vim /etc/man.config
-------------------
MANPATH /yourPath/...
-------------------