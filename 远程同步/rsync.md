## 增量拷贝
> rsync

- 同步
sync ;刷新文件系统缓存，强制将修改过的数据块写入磁盘，并且更新超级块

- 异步
async ;将数据先放到缓冲区，再周期性（一般是30s）同步到磁盘

- 远程同步 remote synchronous
rsync
;可以镜像保存整个目录树和文件系统
;可以保留原有对权限（permission,mode),owner,group,时间（修改时间，modify time),软硬链接，文件acl，文件属性信息等
;传输效率高，使用同步算法，只同步变化的
;支持匿名传输，方便网站镜像，也可以做验证，加强安全

> man rsync
> options
-----------------------------------
-v  详细模式输出
-a  归档模式，递归的方式传输文件，保留文件的属性
-r  递归拷贝目录
-l  保留软链接
-p  保留原有权限
-t  保留原有时间（修改）
-g  保留属组权限
-o  保留属主权限
-D  等于--deviecs --specials 表示支持b（块文件）,c（字符文件，IO设备如/dev/tty1,键盘）,s（socket文件）,p（管道文件）类型文件
-R  保留相对路径
-H  保留硬链接
-A  保留ACL策略
-e  指定要执行的远程shell命令
-E  保留可执行权限
-X  保留扩展属性信息
-----------------------------------
- 本地同步
rsync -av /yourPath/source/ /yourPath/dest
rsync -av --delete /yourPath/source/ /yourPath/dest

- 远程同步
rsync -av /yourPath/source/ userName@ip:/yourPath/dest ;同步本地到远程服务器
rsync -av userName@ip:/yourPath/dest /yourPath/source/ ;从远程服务器同步到本地

- 自动备份daemon服务
> 服务端开启守护进程
vim /etc/rsyncd.conf
-----------------------------------
[appName]
path = /serverPath/dirName
log file = /var/log/rsync.log
;comment = 共享给客户端看的信息，可自定义
;auth users = userName1,userName2
;secrets file = /etc/rsyncd.secrets
;read only = false
;uid = 0 // 代表root
;gid = 0 // 代表root
-----------------------------------
rsync --daemon

> 关闭程序
pkill -9 rsync

> 客户端拉取
- 查看服务端提供的同步模块
rsync -a ip::
-----------------------------------
appName
-----------------------------------
rsync -av rsync://ip/appName /clientPath/dirName/
rsync -av ip::appName /clientPath/dirName/