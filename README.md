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

# Python操作MongoDB
import pymongo

#连接MongoDB
client=pymongo.MongoClient("mongodb://localhost:27017/");
#创建数据库
cnp=client["company"];
#创建集合
emp=cnp["emp"];
#准备数据
#data={"name":"Jackline","age":23,"gender":"female","cameInTime":"2005-3-12","job":"secretary","salary":2000};
##新增：插入数据
#res=emp.insert_one(data);

#data={"name":"Mary","age":23,"gender":"female","cameInTime":"2005-2-12","job":"office lady","salary":2200};
##插入数据
#res=emp.insert_one(data);
#data={"name":"Baby","age":33,"gender":"female","cameInTime":"2007-3-12","job":"asst manager","salary":2100};
##插入数据
#res=emp.insert_one(data);
#data={"name":"Jade","age":23,"gender":"female","cameInTime":"2005-4-12","job":"designer","salary":2500};
##插入数据
#res=emp.insert_one(data);

#print(res);

##新增：插入多条数据
#emps=[
#      {"name":"Dion","age":23,"gender":"female","cameInTime":"2005-4-12","job":"clerk","salary":2300},
#      {"name":"emily","age":23,"gender":"female","cameInTime":"2005-4-12","job":"ol","salary":2400},
#      {"name":"fanny","age":23,"gender":"female","cameInTime":"2005-4-12","job":"researcher","salary":2900}
#    ]
#x=emp.insert_many(emps)

#查询
#查询全部
#for x in cnp.emp.find():
#   print(x)

#查询多个
#qrstr={"name":"Jackline"}
#doc=emp.find(qrstr)
#for x in doc:
#    print(x)

#查询一个
#qrstr={"name":"Jackline"}
#rs=emp.find_one(qrstr)
#print(rs)

#修改一个
#mydata={"name":"Jackline"}
#newVal={"$set":{"salary":1500}}

#emp.update_one(mydata,newVal)

#qrstr={"name":"Jackline"}
#rs=emp.find_one(qrstr)
#print(rs)

#利用正则表达式修改一个或多个
#myQr={"name":{"$regex":"^J"}}
#newVal={"$set":{"salary":1900}}
#res=emp.update_many(myQr,newVal)
#print(res.modified_count,"条数据已经修改")

#删除一条数据
#deldata={"name":"Jackline"}
#result=emp.delete_one(deldata)
#print(result.deleted_count)

#删除多条数据
#deldata={"name":"Jackline"}
#result=emp.delete_many(deldata)
#print(result.deleted_count)

#利用正则表达式删除
#deldata={"name":{"$regex":"^J"}}
#result=emp.delete_many(deldata)
#print(result.deleted_count)

#排序
recs=emp.find().sort("salary")
for x in recs:
    print(x)

