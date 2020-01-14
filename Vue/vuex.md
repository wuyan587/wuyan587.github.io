# vuex

# vuex的简介
vuex包含下面三个要素:
1. state
2. actions
3. mutations

## state
其实也就相当于我们在组件中的date，只不过用了vuex后我们统一用state中的参数了
## mutations
在vuex中，我们如果想要对state中的数据进行相关的操作，那么就需要在mutations中定义相对应的函数
## actions
其实也就是在actions中触发在mutations中定义的函数

具体例子如下：
```js
const store=Vuex.Store({
    state:{
        num:0
    },
    mutations:{
        add(state,val){ //第二个形参可写可不写,这里的state对应的其实就是上面的state,如果不需要从外部传参，那么就可以不用写val
        //（这里的val就是个变量名而已，你喜欢叫啥就叫啥）
            state.num++; //这里我们取到state下面的num这个参数，对他进行加1的操作
            state.num+=val;//这里我们取到state下面的num这个参数，让它加上外面传进来的参数val
        },
        del(state,val){  //这里定义了一个对state里面的num进行-的函数
            state.num--; //这里我们取到state下面的num这个参数，对他进行减1的操作
            state.num-=val;//这里我们取到state下面的num这个参数，让它减去外面传进来的参数val
        }
    },
    actions:{  //其实actions可写可不写,这里面写的是触发mutations里面函数的函数
        add(context){
            context.commit('add') //括号里写的是mutations里面定义的函数的名字，记得加'',
            //如果想要传参，那么写第二个参数，如
            context.commit('add',2) //这里，我传入了一个参数2，对应的也就是mutations里面的add函数的val
        },
        //上面的这种写法其实也可以写出下面这种写法,就是用结构赋值把commit从context中提取出来而已
        add({ commit }){
            commit('add');
        },
        del({commit}){
            commit('del')
        }
    }
})
```
## 创建一个vuex模块

### 安装
yarn add vuex

### 引入vuex
```js
import Vue from 'vue'
import Vuex from 'vuex'
```
### 在Vue中使用vuex
```js
Vue.use(Vuex)
```

### 创建一个store
```js
const store=Vuex.Stroe({
    modules:{    //这里写的是分别管理的vuex
        user,    //如user相关的vuex状态
    }
})
```
### 导出store
```js
export default store;
```

## 在vue中全局注册vuex

**进入到main.js中**

导入刚才写的vuex模块
```js
import store from './store' //上面创建的store模块
```
在下面这段代码中注册，如下
```js
new Vue({
    router,
    store,
    render: h => h(App),
}).$mount('#app')
```

