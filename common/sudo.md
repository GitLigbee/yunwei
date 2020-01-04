#### sudo

> 修改配置文件
`visudo`
`vim /etc/sudoers`

> 普通账户获取root权限
`userName   ALL=(ALL)       ALL`

> 普通账户无密码获取root权限
`userName   ALL=(ALL)       NOPASSWD:ALL`