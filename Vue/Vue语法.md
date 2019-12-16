# Vue语法

### 数据响应原理

Vue的数据响应原理通过数据拦截，运用ES5的Object.defineProperty(),通过getter和setter来实现

```js
Object.defineProperty(obj,'属性名',{
    get:function(){
        return 'value'; //通过拦截初始化的数据，并设置为自定义的数据
    },
    set:function(value){
        innerHTML=value;    //将实例里面的数据修改为用户传入的数据
    }
})
```

### 创建一个Vue实例

```js
new Vue({
    el:element,//这里存放的是实例的元素对象
    data:{  //这里存放的是实例里面的数据

    },
    methods:{ //这里存放的是实例里面的方法

    }
})


```

### 插值表达式

想要输出vue里的变量到html中需要用到插值表达式
{{变量名}}
插值表达式里能输出的
```js
{{对象:{}}}
{{数组:[]}}
{{函数的结果:fn(){
    return '结果'
}}}
{{字符串:'string'}}
{{数字:1}}
{{'undefined':undefined}}
{{'null':null}}
{{布尔值:true}}
```

### Vue的条件判断

```js

v-if= 
v-if= v-else=
v-if= v-else-if= v-else=
v-show=

```
v-show v-if的差别为
v-if为false时则直接不渲染这个元素，而v-show则是通过设置元素的display的值来改变元素的显示与否
v-if的性能优势比v-show高，但是当一个元素需要**<font color='red'>频繁</font>**的出现和消失时更推荐使用v-show。


### Vue的循环

```javascript
v-for='item of arr' //item为数组或对象的值
v-for='item in arr' //item为数组或对象的值

<ul>
    <li v-for='(item,index) in arr' v-bind:key='index' > //在遍历的时候，推荐加上key值
    
    {{item}} //这里的item为数组的值
    </li>
</ul>
     //渲染出数组的值的个数个的li

//如果需要索引，则使用
v-for='(item,index) of arr' //item为数组或对象的值，而index为数组的索引或对象的属性

//如果需要在遍历对象的时候再获取索引
v-for='(item,key,index) of obj' //item为对象的属性值，而key对象的属性，index为对象的索引。
```

### Vue里对数组进行的操作

当对data里面的数组进行操作时，需要注意以下两点
1. 直接对数组的length进行改变的时候，视图(V)并不会随着改变而改变，但是数据确实会改变
```js
//如
arr.length=0;//这样直接将数组的length设置为0
```
2. 直接对数组的索引进行改变时，也就是如 arr[index]=1;这样直接设置某个索引的值的时候，视图(V)也并不会随着改变而改变，但是数据确实会改变。

所以如果需要通过索引改变数组的值的时候，需要用到Vue.set(arr,index,value);这个方法 --内部封装了Object.assign()这个方法

### v-model

v-model这个值**<font color='red'>只能在表单</font>**里使用，也就是相当于绑定了表单input框的value值
```javascript
<input v-model='val'> 

new Vue({
    data:{
        val:''
    }
})
```