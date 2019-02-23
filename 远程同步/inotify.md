## inotify 实时同步

- install
```
tar xf inotify-tools-{version}.tar.gz && cd inotify-tools-{version}
./configure
make && make install
;/usr/local/bin/inotifywait
;/usr/local/bin/inotifywatch
```

- useage
```
inotifywait --help
-----------------------
-m 保持监控状态
-r 递归
-q 只打印事件
-e 指定事件
    ;事件：
    moved 移动
    delete 删除
    create 创建
    modify 修改
    attrib 属性信息
-----------------------
```
- 编写脚本实现监控目录
```
vim /yourPath/wait.sh
-----------------------
#!/bin/bash
/usr/local/bin/inotifywait -mrq -e moved,modify,delete,create,modify,attrib /dirClient |while read events
    do
        rsync -a --delete /dirClient /dirServer
        echo "`date +%F\ %T`出现事件$events" >> /var/log/rsync.log 2>&1
    done
-----------------------
chmod +x /yourPath/wait.sh
/yourPath/wait.sh &
```