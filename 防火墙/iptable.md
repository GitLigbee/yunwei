### iptable
> linux 系统内核集成了网络访问控制的功能，通过netfilter模块来实现，是内核的一部分（内核空间）
用户空间可以通过iptable对netfilter进行控制管理，进而实现网络对访问控制。

1. 数据包过滤 (filter)
2. 网络控制 (filter)
3. 地址转换（源地址和目标地址）(nat)

结构
表 》 链 》 规则
表：
filter
nat 
mangle
raw

链：
PREROUTING
INPUT
OUTPUT
FORWARD
POSTROUTING

// 查看表.链
iptables -t filter -L