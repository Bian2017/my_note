## MongoDB 常用相关指令

1. 指令 show dbs

检查可用数据库的列表。

> show dbs

```
admin           0.000GB
config          0.000GB
local           0.000GB
node_community  0.000GB
```

2. 指令 use

MongoDB 使用 use DATABASE_NAME 命令来创建数据库。如果指定的数据库 DATABASE_NAME 不存在，则该命令将创建一个新的数据库，否则返回现有的数据库。

```
> use node_community
switched to db node_community
```

3. dropDatabase()方法

dropDatabase()方法用于删除数据库。如果要删除新数据库 node_community，那么 dropDatabase()命令将如下所示：

```
> use node_community
switched to db node_community

> db.dropDatabase()
{ "dropped" : "node_community", "ok" : 1 }
```

4. show collections

show collections 用于检查创建的集合。

```
> show collections
users
```

5. getIndexes()方法

getIndexes()方法可以用来查看集合的所有索引。

```
> db.users.getIndexes()
[
	{
		"v" : 2,
		"key" : {
			"_id" : 1
		},
		"name" : "_id_",
		"ns" : "node_community.users"
	},
	{
		"v" : 2,
		"unique" : true,
		"key" : {
			"name" : 1
		},
		"name" : "name_1",
		"ns" : "node_community.users",
		"background" : true
	}
]
```
