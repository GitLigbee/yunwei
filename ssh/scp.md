### 远程拷贝

- 拷贝至远程服务器
scp /clientPath/fileName userName@ip:/serverPath/

- 拷贝至本地
scp userName@ip:/serverPath/fileName /clientPath/ ;文件
scp -r userName@ip:/serverPath/dirName /clientPath/ ;目录