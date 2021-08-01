# Learn-MongoDB
mongodb 学习

安装MongoDB压缩版：
安装MongoDB-windows-4.0.25
1.下载：https://fastdl.mongodb.org/win32/mongodb-win32-x86_64-2008plus-ssl-4.0.25.zip

2.将zip文件解压缩到E:\mongodbw-4.0（可以根据实际修改路径）

3.将E:\mongodbw-4.0\bin路径添加到环境变量path中。

4.在E:\mongodbw-4.0\目录下面创建一个叫data的目录，在data目录里面创建一个db目录和一个log目录


5.在E:\mongodbw-4.0\bin\下面创建一个叫mongod.cfg文件，内容如下（路径可以根据需要修改）：
systemLog:
  destination: file
  path: E:\mongodbw-4.0\data\log\mongod.log
  logAppend: true
storage:
  journal:
    enabled: true
  dbPath:  E:\mongodbw-4.0\data\db
net:
  #bindIpAll: true
  bindIp: 0.0.0.0
  port: 27017
#security:
  #authorization: enabled
  
6.安装MongoDB服务：以管理员身份运行cmd，在打开的窗口中输入：
   mongod.exe --config “E:\mongodbw-4.0\bin\mongod.cfg” --install
   
7.开启mongodb服务：net start mongodb

看到
MongoDB 服务正在启动 .
MongoDB 服务已经启动成功。
说明安装成功
