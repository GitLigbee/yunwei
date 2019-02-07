- 添加用户组
groupadd groupName

- 添加用户到对应组
gpasswd -a userName groupName
- 查看用户所属
tail /etc/group