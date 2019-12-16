# Vue事件

### Vue的普通事件写法
```javascript
//普通事件的写法
<button v-on:click='fn'>按钮</button>//这里的fn就是事件处理函数
//button @click='fn'>按钮</button>  v-on可以简写为@
new Vue({
    methods:{
        fn(){
            console.log('事件处理函数');
        }
    }
})
//如果需要对事件对象进行处理
<button v-on:click='fn'>按钮</button>

new Vue({
    methods:{
        fn(e){
            console.log('事件对象',e);//e就是事件对象，Vue的事件对象就是原生的事件对象。
        }
    }
})
//如果需要在事件函数里传参
<button v-on:click='fn(a,b)'>按钮</button>//在这里的函数后面的括号里进行传参

new Vue({
    methods:{
        fn(a,b){
            console.log(a+b);
        }
    }
})
//如果又需要事件对象又需要传参
<button v-on:click='fn($event,a,b)'>按钮</button>//那么就在这边的括号里加入一个$event,这个就是事件对象

new Vue({
    methods:{
        fn(e,a,b){
            console.log(e);//这里的e就是事件对象
            console.log(a+b);//这里的a，b就是其他传入的参数
        }
    }
})

```

### Vue事件的各种修饰符

```javascript
<div v-on:click='fn1'>大盒子
    <div v-on:click='fn2'> 中盒子
        <div v-on:click='fn3'>小盒子
        </div>
    </div>
</div>

new Vue({
    methods:{
        fn1(){
            console.log('大盒子');
        },
        fn2(){
            console.log('中盒子');
        },
        fn3(){
            console.log('小盒子');
        }
    }
})

```
如上图所示，Vue的事件里面存在事件冒泡和默认行为，所以为了阻止事件冒泡和取消默认行为，Vue加入了一下事件的修饰符

```javascript
v-on:click.stop='fn'   //这里的stop就是阻止事件冒泡 stopPropagation 取前面的stop  常用
v-on:click.prevent='fn'   //这里的stop就是阻止默认行为 preventDefault  取前面的prevent 常用
v-on:click.once='fn'  //这里的once指的是这个事件就执行一次，之后不会再触发 常用
v-on:click.self='fn'  //这里的self指的是只有触发当前元素才会执行函数，相当于阻止事件冒泡
```

### 按键事件的修饰符

为了简化按键的操作，也就是简化掉e.keyCode==这步操作，Vue也加入了按键的修饰符
```javascript

v-on:keyup.enter='fn' //这里的enter键就是指的按下enter键才触发事件
v-on:keyup.13='fn'  //这里的13指的是enter键的ascll码，指的按下enter键才触发事件
```