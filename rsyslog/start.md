### Getting started

> install
```
;系统默认已安装
> rpm -q rsyslog
rsyslog-8.24.0-41.el7_7.x86_64

> rpm -ql rsyslog
/etc/rsyslog.conf ;配置文件
```

> 配置
- 日志定义相关符号

|符号|说明|举例|
|---|---|---|
|.|用来分隔服务和日志级别|mail.info|
|*|任何服务,或者任何级别|\*.info mail.*|
|=|有等号表示等于某一日志级别,没有等号表示大于或者等于某一级别|mail.= info|
|!|排除操作,前面有相同服务的表达式,这个操作才有意义,代表从前面表达式所包含的内容中排除某些内容||
|;|用于分隔不同的服务,级别组合|cron.=info;mail.info|
|,|用于分隔不同的服务|cron,mail. =info|
|-|用于指定目标文件时,代表异步写入|-/var/log/ maillog|

> 测试
`logger`用于往系统中写入日志，提供了一个shell命令接口到rsyslog系统模块
```
> logger -it "test log" -p cron.info "test cron"
-i 逐行记录每一次logger的进程ID
-t 指定标记记录
-p 指定输入消息的优先级，优先级可以是数字或者指定为{facility}.{level}
```