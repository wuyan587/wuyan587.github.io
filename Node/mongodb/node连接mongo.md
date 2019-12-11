# mongodb

#### 安装mongodb模块
```javascript
    npm install mongodb -S
```

#### 引入模块并初始化
```javascript
    const mongodb=require('mongodb').MongoClient;
```
#### 设置数据库链接地址
```javascript
    const url='mongodb://localhost:27017';
```
#### 设置需要连接的数据库的名称
```javascript
    const dbname='admin'; //链接到admin数据库
```
#### 设置需要连接的数据库下面的表名
```javascript
    const tablename='user';
```
#### 建立连接
```javascript
    mongodb.connect(url,(err,client)=>{});
```
#### 连接到对应的数据库
```javascript
    const db=client.db(dbname);
```
#### 连接到对应的表
```javascript
    const tables=db.collection(tablename);
```
#### 查找数据
```javascript
    //db.表名.find({这里面可以放条件})
    tables.find().toArray((err,data)=>{
        console.log(data); //data就是查询到的数据，为json的格式
    })
```
#### 添加数据
##### 			添加一条
```javascript
    tables.insertOne({name:'李四'}); //插入一条name值为李四的数据
```
##### 			添加多条
```javascript
    tables.insertMany([{name:李四}，{name:张三});//插入两条数据
```
#### 更新数据
##### 			更新一条	
```javascript
    tables.updateOne({name:'李四'},{$set:{age:30}});//更新name值为李四的数据的age值为30，多条匹配则只更新一条
```
##### 			更新多条
```javascript
    tables.updateMany({name:'李四'},{$set:{age:30}});//更新全部name值为李四的数据
```
#### 删除数据
##### 			删除一条
```javascript
    tables.deleteOne({name:'李四'}); //删除name值为李四的数据,多条匹配只删除第一条
```
##### 			删除多条
```javascript
    tables.deleteMany({name:'李四'}); //删除全部name值为李四的数据
```

# 总的代码为
```javascript
    //初始化 mongodb模块
    const mongodb=require('mongodb').MongoClient;
    //mongodb的链接地址
    const url='mongodb://localhost:27017';
    //你要连接的mongodb的数据库名称
    const dbname='admin';
    //你要连接的表名
    const tablename='user';
    //连接mongodb
    mongodb.connect(url,(err,client)=>{
        //连接库
        const db=client.db(dbname);
        //连接表
        const tables=db.collection(tablename);
        //查询数据
        tables.find().toArray((err,data)=>{
            console.log(data);
        })
        //增加数据
        tables.insertOne({name:'李四'}); //增加一条
        tables.insertMany([{name:李四}，{name:张三});//插入多条数据
        //更新数据（修改数据）
        tables.updateOne({name:'李四'},{$set:{age:30}});//修改匹配的第一条
        tables.updateMany({name:'李四'},{$set:{age:30}});//修改全部匹配的数据
        //删除数据
        tables.deleteOne({name:'李四'});  //删除第一条匹配的数据
        tables.deleteMany({name:'李四'}); //删除全部匹配的数据
    })
```