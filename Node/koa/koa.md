# koa

### 什么是koa
koa 是由 Express 原班人马打造的，致力于成为一个更小、更富有表现力、更健壮的 Web 框架。

### 安装
koa需要node7以上版本
```js
npm install koa
```

### 创建服务器
```js
const Koa =require('koa');
const app=new Koa();
const host='127.0.0.1';
const port=2002;

//koa使用中间件的方式
app.use(async (ctx,next)=>{
    ctx.body=1;  //发送给服务端信息 ctx.body=????
 
})
//监听端口
app.listen(port,host,()=>{
    console.log(`服务运行在http://${host}:${port}`);
});//服务器运行在 http://127.0.0.1:2002
```

### 级联
```js
//koa中间件运用await next()来进行下一个中间件的执行
app.use(async (ctx,next)=>{
    ctx.body=1; 
    await next();//没有 await next()则只执行到这句，也就是输出1;
 
})
app.use(async (ctx,next)=>{
    ctx.body=2;
    await next();//没有 await next()则只执行到这句，也就是输出2;
})
app.use(async (ctx,next)=>{
    ctx.body=3;
    ctx.body=ctx;
})

```

### 运用koa建立多个服务器
```js
const http = require('http');
const https = require('https');
const Koa = require('koa');
const app = new Koa();
http.createServer(app.callback()).listen(3000); //创建一个端口为3000的服务器
https.createServer(app.callback()).listen(3001);//创建一个端口为3001的服务器
```

### koa的错误处理
```js
app.on('error',err=>{
    console.log(err);  //运用一个错误事件去处理报错
})
```

### koa Context (ctx)
koa Context就是request和response的结合体
```js
{
	"request": {
		"method": "GET",  //请求方式
		"url": "/",       //请求的地址
		"header": {        //请求头的信息
			"host": "127.0.0.1:2002",
			"connection": "keep-alive",
			"cache-control": "max-age=0",
			"upgrade-insecure-requests": "1",
			"user-agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.108 Safari/537.36",
			"sec-fetch-user": "?1",
			"accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3",
			"sec-fetch-site": "none",
			"sec-fetch-mode": "navigate",
			"accept-encoding": "gzip, deflate, br",
			"accept-language": "zh-CN,zh;q=0.9"
		}
	},
	"response": {     
		"status": 200,
		"message": "OK",
		"header": {
			"content-type": "application/json; charset=utf-8"
		}
	},
	"app": {
		"subdomainOffset": 2,
		"proxy": false,
		"env": "development"
	},
	"originalUrl": "/",
	"req": "<original node req>",
	"res": "<original node res>",
	"socket": "<original node socket>"
}
```
### ctx.request
Koa 的 Request 对象。

**req.header** 请求头对象
**req.header=**  设置请求头对象
**req.method** 请求方式
**req.method=** 设置请求方式
**req.length** 以数字的形式返回 request 的内容长度(Content-Length)，或者返回 undefined。
**req.url** 获得请求url的地址
**request.url=**  设置请求地址，用于重写url地址时
**request.origin** 获取URL原始地址, 包含 protocol 和 host

```js
ctx.request.origin
// => http://example.com
```
**request.href** 获取完整的请求URL, 包含 protocol, host 和 url
```js
ctx.request.href;
// => http://example.com/foo/bar?q=1
```
**request.querystring** 获取查询参数字符串(url中?后面的部分)，不包含?
**request.query** 
将查询参数字符串进行解析并以对象的形式返回，如果没有查询参数字字符串则返回一个空对象。注意：该方法不支持嵌套解析。
```js
//例如 "color=blue&size=small":
    {
    color: 'blue',
    size: 'small'
    }
```
**request.is(types...)**

```js
检查请求所包含的 "Content-Type" 是否为给定的 type 值。 如果没有 request body，返回 undefined。 如果没有 content type，或者匹配失败，返回 false。 否则返回匹配的 content-type。

// With Content-Type: text/html; charset=utf-8
ctx.is('html'); // => 'html'
ctx.is('text/html'); // => 'text/html'
ctx.is('text/*', 'text/html'); // => 'text/html'

// When Content-Type is application/json
ctx.is('json', 'urlencoded'); // => 'json'
ctx.is('application/json'); // => 'application/json'
ctx.is('html', 'application/*'); // => 'application/json'

ctx.is('html'); // => false
比如说您希望保证只有图片发送给指定路由

if (ctx.is('image/*')) {
  // process
} else {
  ctx.throw(415, 'images only!');
}
```
### ctx.response
Koa 的 Response 对象。

**response.header** Response header 对象。
**response.headers** Response header 对象。等价于 response.header.
**response.socket** Request socket.
**response.status**
获取响应状态。 默认情况下，response.status设置为404，而不像node's res.statusCode默认为200。
**response.status=** 通过数字设置响应状态:

