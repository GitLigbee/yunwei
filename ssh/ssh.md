### 远程登录服务器
> ssh --help

- 登录
ssh ip ;默认使用当前登录用户名作为需要登录的远程服务器用户,默认使用22端口
ssh userName@ip ;使用userName登录远程服务器
ssh -l userName ip
ssh -l userName ip -p 22

- 修改配置
vim /etc/ssh/sshd_config
;禁止root远程登录
;修改默认端口

- 生成密钥对
ssh-keygen
- 将公钥发送给远程服务器用户，保存至authorized_keys
ssh-copy-id -i userName@ip