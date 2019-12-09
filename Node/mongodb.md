# mongodb

#### 	查看数据库

​	**show dbs**

#### 	切换数据库

​	**use 库名**    -如果没有这个数据库会自动创建

#### 	选择集合并进行操作

​	**db.集合名.**

#### 	插入数据

​	**db.集合名.insert({key:value,key2:value2})**

​	**db.集合名.save({key:value,key2:value2})**

#### 	删除数据

​	**db.集合名.remove({})**  -里面空对象的话删除全部数据

​	**db.集合名.remove({key:value})**  -删除条件匹配的全部数据

#### 	<font color='red'>修改数据</font>

​	**db.集合名.updata({key:value},{$set:{key2:value2}},true,true)**

​	修改符合条件的全部数据

​	**db.集合名.updata({条件的键名:条件的键值},{$set:{设置的键名:设置的键值}},true,true)**

​	第一个参数表示**查找的条件**，第二个参数表示**修改内容**，第三个参数表示**匹配全部符合条件的数据**，第四个参数表示**修改全部符合条件的数据**

#### 	<font color='red'>查询数据</font>

​	**db.集合名.find()**  -括号里为空，则查找全部数据。

​	**db.集合名.find({key:value})**  -查找符合条件的全部数据

​	**db.集合名.findOne({key:value})**   -查找符合条件的一条数据

#### 各种条件

​	大于： {$gt:value}

​	小于：{$lt:value}

​	大于等于：{$gte：value}

​	小于等于：{$lte:value}

#### 排序

​	**.sort({key:-1})**  按条件降序排列

#### 切割

​	**.limit(number)**  -从前开始切割出number条数据

#### 跳过

​	**.skip(number)**  -从前开始跳过number条数据