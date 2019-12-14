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
v-if的性能优势比v-show高，但是当一个元素需要频繁的出现和消失时更推荐使用v-show。


### Vue的循环

```js
v-for='item of arr' //item为数组或对象的值
v-for='item in arr' //item为数组或对象的值

//如果需要索引，则使用
v-for='(item,index) of arr' //item为数组或对象的值，而index为数组的索引或对象的属性

//如果需要在遍历对象的时候再获取索引
v-for='(item,key,index) of obj' //item为对象的属性值，而key对象的属性，index为对象的索引。
```