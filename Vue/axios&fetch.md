# axios和fetch

### axios和fetch
这两个都是用来发送请求的，不同的是axios是别人封装的，需要下载模块，而fetch是原生封装的，所以fetch的兼容更强大

## axios

### 安装axios

npm install axios -S

### axios的传输方式
axios的方式有以下几种
- axios.get(url,option)
- axios.post(url,option)
- axios.put(url,option)
- axios.delete(url,option)
- axios(option)

### axios语法
语法如下
```javascript
axios.defaults.baseURL='' //默认的地址，但设置的时候，跟参数里的url拼接 为完整地址

//当请求方式为get,put,delete时
axios({
    method:'get'，//请求方式，默认的参数是get，也可以填post，put，delete
    url:'',//请求的地址
    params:{ //当请求方式为get，put，delete时，参数放在params里进行传输，为键值对的形式
        key:value,
        key2:value2,
    }
}).then(data=>{console.log(data)})//axios是用promise封装的，所以通过then的方法来进行后续的处理。
    .catch(err=>console.log(err))//promise用catch来对错误进行处理

//当请求方式为post时
axios({
    method:'post'，//请求方式，默认的参数是get，也可以填post，put，delete
    url:'',//请求的地址
    data:{ //当请求方式为post时，参数放在data里进行传输，为键值对的形式
        key:value,
        key2:value2,
    }
}).then(data=>{console.log(data)})//axios是用promise封装的，所以通过then的方法来进行后续的处理。
    .catch(err=>console.log(err))//promise用catch来对错误进行处理
```

### post的两种方式

1. 使用json的格式进行发送
```javascript
axios({
    method:'post'，//请求方式，默认的参数是get，也可以填post，put，delete
    url:'',//请求的地址
    data:{ //当请求方式为post时，参数放在data里进行传输，为键值对的形式
        key1:value1,
        key2:value2,
    }
}).then(data=>{console.log(data)})//axios是用promise封装的，所以通过then的方法来进行后续的处理。
    .catch(err=>console.log(err))//promise用catch来对错误进行处理

```
当使用这种形式进行传输数据的时候，默认为json格式，这时候查看f12的network可以看到
content-type: application/json; charset=utf-8
数据放在  Request Payload 里进行传输


2. 使用表单的形式进行传输
```javascript
const p=new URLSearchParams();
p.append(key1,value1);
p.append(key2,value2);
axios({
    method:'post'，//请求方式，默认的参数是get，也可以填post，put，delete
    url:'',//请求的地址
    data:p //p里面就是传输的数据
}).then(data=>{console.log(data)})//axios是用promise封装的，所以通过then的方法来进行后续的处理。
    .catch(err=>console.log(err))//promise用catch来对错误进行处理

```
使用这种形式进行数据传输的时候
content-type:application/x-www-form-urlencoded;charset=utf-8
数据放在  form-data   里进行传输