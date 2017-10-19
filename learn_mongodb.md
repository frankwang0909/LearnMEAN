# MongoDB 学习笔记 (一）

## 下载、安装

1.[官网](https://www.mongodb.com/download-center?jmp=tutorials&_ga=2.240842883.105177426.1508318606-1068482157.1506065532#community)下载 安装文件, 选择 Window 64 位的版本  `Windows Server 2008 R2 64-bit and later, with SSL support x64`



2.点击下载好的 `mongodb-win32-x86_64-2008plus-ssl-3.4.9-signed..msi` 文件，

默认安装在 `C:\Program Files\MongoDB\Server\3.4\`。



## 运行

1.创建目录，并指定数据库地址。
```shell
"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe" --dbpath G:\mongodb\data
```

2.启动 MongoDB

在命令行中输入以下命令：
```shell
"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe"
```

正确启动，最后一行将会显示类似于如下信息，默认端口 27017：

	2017-10-18T18:37:41.512+0800 I NETWORK  [thread1] waiting for connections on port 27017


如果用浏览器打开 [localhost:27017](localhost:27017)，显示:

	It looks like you are trying to access MongoDB over HTTP on the native driver port.

## 为 MongoDB 配置 window 服务

1.打开命令行工具

2.在 `G:\mongodb\data` 中创建以下两个目录：
```shell
mkdir db
mkdir log
```

3.在 安装目录下（`C:\Program Files\MongoDB\Server\3.4\`）新建一个配置文件 `mongod.cfg`， 指定存放数据和日志的目录。
```
systemLog:
    destination: file
    path: G:\mongodb\data\log\mongod.log
storage:
    dbPath: G:\mongodb\data\db
```

4.安装 MongoDB 服务

在命令行工具中输入以下命令（管理员权限）：
```shell
"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe" --config "C:\Program Files\MongoDB\Server\3.4\mongod.cfg" --install
```

5.启动 MongoDB 服务
```shell
net start MongoDB
```

6.终止或移除 MongoDB 服务

终止MongoDB 服务：
```shell
net stop MongoDB
```


移除MongoDB 服务：
```shell
"C:\Program Files\MongoDB\Server\3.4\bin\mongod.exe" --remove
```



## 参考资料

- 1. [https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/](https://docs.mongodb.com/manual/tutorial/install-mongodb-on-windows/)
