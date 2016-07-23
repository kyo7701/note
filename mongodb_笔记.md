### mongodb 笔记

#### 1.mongodb的安装

```
brew install mongodb 

```

#### 2.配置

配置好mongodb后,就需要对mongodb的dbpath进行配置，将db存储到指定的dbpath中

```
mongod -dbpath [your path name]

```

#### 3.基本概念


- database 	数据库
- collection 集合
- document 文档

#### 4.常用操作

##### 创建集合(创建表)

```
use dataBaseName;
db.createCollection('Collectionname');
```
##### 删除集合

```
db.CollectionName.drop();   //删除成功会返回true;
```


##### 查询

```
db.dbname.find()  //equals to  select * from tableName 
```
- #### 条件查询(where >= <= > < ==)
##### 查询 student表中age < 23的记录
```
db.student.find(age:{$lt:23})
```
##### 查询 student表中age > 23的记录
```
db.student.find(age:{$gt:23})
```
##### 查询 student表中age >= 23的记录
```
db.student.find(age:{$gte:23})
```
##### 查询 student表中age <= 23的记录
```
db.student.find(age:{$lte:23})
```
##### 查询 student表中age == 23的记录
```
db.student.find(age:23)
```

##### 插入指定记录
mongodb在存储时使用bson格式,插入纪录就像在拼接一个json串.其中mongodb默认主键为_id.

```
db.student.insert({"name":"24k","age",23})
```
##### 删除指定记录
删除名称为24k的记录

```
db.student.remove({"name":"24k"})
```

