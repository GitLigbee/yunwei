### yum 命令

- 默认是安装来自仓库的软件，指定的是软件名字，多个空格隔开。-y (取消交互)
yum install packageName -y

- 安装来自本地路径的rpm包
yum install yourPath/packageName.rpm
; yum localinstall yourPath/packageName.rpm

- 卸载软件包
yum remove / erase packageName

- 升级所有包，同时也升级软件和系统内核
yum -y update

- 只升级包
yum -y upgrade

- 指定升级的软件
yum update packageName

- 搜索包含关键字的软件
yum search keyWord

- 找出模块由哪些软件包提供
yum provides "*name.so*"

- 搜索一个包含关键字的软件包
yum provides "*name*"

- 清空之前的yum列表缓存
yum clean all

- 创建新的缓存
yum makecache

- 列出仓库里的所有软件包
yum list

- 列出已配置的软件仓库
yum repolist

- 查看未安装的软件包
yum list | tail

- @代表已经安装成功
yum list | grep keyWord

- 查看已经安装的软件包
yum list installed

- 查看包组
yum grouplist

- 安装包组
yum groupinstall "包组"

- 卸载包组
yum groupremove "包组"

- 