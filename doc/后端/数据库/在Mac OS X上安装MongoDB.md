**参考：**

[How to install MongoDB on Mac OS X](http://www.codebind.com/mongodb/install-mongodb-mac-os-x/)

## 一、下载后缀名为.tgz 的 MongoDB 压缩包

访问 MongoDB 官网，下载后缀名为.tgz 的 MongoDB 压缩包。解压该文件，并将 mongo 目录移到/usr/local/mongodb 目录下。

```Shell
$ cd ~/Download
$ tar -zxvf mongodb-osx-ssl-x86_64-3.6.1.tgz
$ sudo mv mongodb-osx-ssl-x86_64-3.6.1 /usr/local/mongodb
```

## 二、创建 MongoDB 数据目录(/data/db)

MongoDB 默认将数据存储至/data/db 目录下，需手动创建该目录并且设置相应权限。

```Shell
$ sudo mkdir -p /data/db
$ whoami
codebind
$ sudo chown codebind /data/db
```

## 三、在~/.zshrc 文件中设置 mongodb/bin 路径

为 MongoDB 设置环境变量，这样终端才能识别 mongo 和 mongod 命令。

```Shell
$ cd
$ pwd
/Users/codebind
$ vi .zshrc
```

在.zshrc 文件下的末尾处添加如下命令：

```Shell
export MONGO_PATH=/usr/local/mongodb
export PATH=$PATH:$MONGO_PATH/bin
```

重启终端，通过如下命令验证 mongodb 版本：

```Shell
mongo -version
MongoDB shell version: 3.6.1
```

## 四、启动 MongoDB

首先需运行 mongod 命令，来启动 mongo 守护进程。

先打开两个不同的终端

**终端 1**

运行如下命令：

```Shell
$ mongod
MongoDB starting : pid=38042 port=27017 dbpath=/data/db/ 64-bit host=codebind.local3
//...
waiting for connections on port 27017
```

#### 终端 2

运行如下命令：

```Shell
$ mongo
MongoDB shell version: 3.6.1
connecting to: test
> show dbs
local	(empty)
admin	(empty)
```
