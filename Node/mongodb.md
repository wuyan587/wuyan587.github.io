# mongodb

#### 	查看数据库

```javascript
 show dbs
```



#### 	切换数据库

```javascript
use 库名    //如果没有这个数据库会自动创建
```



#### 	选择集合并进行操作
```javascript
	db.集合名.
```
#### 	插入数据
```javascript
	db.集合名.insert({key:value,key2:value2})

​	db.集合名.save({key:value,key2:value2})
```
#### 	删除数据
```javascript
	db.集合名.remove({})  //里面空对象的话删除全部数据

​	db.集合名.remove({key:value})  //删除条件匹配的全部数据
```
#### 	<font color='red'>修改数据</font>
```javascript
	db.集合名.updata({key:value},{$set:{key2:value2}},true,true)

​	//修改符合条件的全部数据

​	db.集合名.updata({条件的键名:条件的键值},{$set:{设置的键名:设置的键值}},true,true)
```
​	第一个参数表示**查找的条件**，第二个参数表示**修改内容**，第三个参数表示**匹配全部符合条件的数据**，第四个参数表示**修改全部符合条件的数据**

#### 	<font color='red'>查询数据</font>
```javascript
	db.集合名.find()  //括号里为空，则查找全部数据。

​	db.集合名.find({key:value})  //查找符合条件的全部数据

​	db.集合名.findOne({key:value})   //查找符合条件的一条数据
```
#### 各种条件
```javascript
	大于： {$gt:value}

​	小于：{$lt:value}

​	大于等于：{$gte：value}

​	小于等于：{$lte:value}
```
#### 排序
```javascript
	.sort({key:-1})  //按条件降序排列
```
#### 切割
```javascript
	.limit(number)  //从前开始切割出number条数据
```
#### 跳过
```javascript
	.skip(number)  //从前开始跳过number条数据
```

#### 配置mongodb

##### 	配置环境

​	在计算机上右键选择**属性**，选择**高级系统设置**，选择**高级**，点开**环境变量**，选择**系统变量**一栏，点击**变量名为Path**的那栏，选择**编辑**，**添加**，加入mongodb安装目录的**bin路径**，如C:\Program Files\MongoDB\Server\3.2\bin

##### 	启动服务

```javascript
mongod  --storageEngine mmapv1 --dbpath "d:\mongodb\db" --logpath "d:\mongodb\log\MongoDB.log"
```

后面的**dbpath**和**logpath**为数据库和日志储存路径，需**自己创建**

##### 	登记为window服务(开机自启)

```javascript
mongod  --storageEngine mmapv1 --dbpath "d:\mongodb\db" --logpath "d:\mongodb\log\MongoDB.log" --install --serviceName "MongoDB"
```

##### 	登记完成后

```javascript
NET START MongoDB
```

##### 	开始操作数据库

​	运行cmd 输入 mongo