# forEach,for in,for of三者的区别

### forEach

​	forEach是ES5新增的遍历数组的方法，其结构为
```javascript
arr1.forEach((value,index,arr)=>{
    console.log(value); //value为数组的值
    console.log(index); //index为数组的索引
    console.log(arr); //arr的值就是其数组本身
})
```
#### <font color='red'> 缺点 </font>
​	1.forEach不支持break,return 不能跳出循环

### for in
​	for in大部分时间都是被用在遍历对象上，结构为
```javascript
//遍历对象的时候
for(let key in obj){
    console.log(obj[key]);//key为对象的属性
}
//遍历数组的时候
for(let index in arr){
    console.log(arr[index]);//index为数组的索引
}
```

#### <font color='red'>缺点</font>
​	1.for in遍历数组的时候，遍历的顺序是乱的。
​	2.for in遍历数组的时候，会遍历自定义索引。
​	3.for in遍历的时候，索引的类型是string。
不推荐用来遍历数组

### for of
​	for of 是ES6新增的遍历方法，有着同for in一样简洁的语法，却没有那些缺点，不同于forEach，可以中断循环，可以遍历所有具有Iterator接口的数据类型。（除对象以为）

```javascript
    //遍历数组
    for(let value of arr){
        console.log(value); //value值为数组的值而非索引
    }
    //遍历字符串
    for(let value of 'abcd'){
        console.log(value); //输出 a,b,c,d
    }
```

#### <font color='red'>缺点</font>
​	1.没法获取索引！想要获取索引需要用到entries()。

​	*entries() 方法返回一个数组的迭代对象，该对象包含数组的键值对 (key/value)。*

```javascript
    //遍历数组
    for(let [index,value] of arr.entries()){
        console.log(index,value); 
    }
```
​	2.没法遍历对象。