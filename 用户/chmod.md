## 修改权限
### 普通权限、 高级权限、 默认权限、 ACL控制策略

#### 普通权限
r: 4
w: 2
x: 1

- 修改组权限
chmod g+w /youtPath/dirName/

#### 高级权限
- 冒险位（set uid）:4000 针对的是一些命令，临时拥有文件的拥有者权限
chmod u+s /usr/bin/vim
chmod 4755 /usr/bin/vim

- 强制位（set gid)：2000 一般针对的是公共目录，如果该目录拥有强制位，意味着任何用户在该目录下创建的文件，强制继承该目录的所属组
chmod g+s /yourPath/dirName/

- 粘滞位（sticky bit): 1000 一般针对的是公共目录，如果该目录拥有粘滞位，意味着只有root和创建者能删除自己创建的文件，其它用户只能自己管理自己的文件
chmod o+t /yourPath/dirName/