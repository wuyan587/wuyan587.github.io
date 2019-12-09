# Http

```javascript
    //引入模块
    const http=require('http');
    //设置端口
    const port=3030;
    let data='';
    //创建服务
    http.creatServer((req,res)=>{
        //设置响应头
        res.writeHead(200, {'Content-Type':'text/html'});
        //响应信息
        res.write();
        //结束响应
        res.end();
        //接受到post请求,获取数据
        req.on('data',chunk=>{
            data+=chunk;
        })
        //post请求结束
        req.on('end',()=>{
            console.log(data);
        })
        //获取请求方式
        console.log(req.method);//'GET,POST'
        //获取请求的地址如'/login'
        console.log(req.url);
    }).listen(port,()=>{  //监听端口
        console.log(`服务器运行在:localhost:${port}`);
    })
```

