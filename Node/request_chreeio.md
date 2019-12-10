# request,chreeio
### 安装request和cheerio模块
    npm install request -S
    npm install cheerio -S
```javascript
//引入模块
const request=require('request');
const cheerio=require('cheerio');
//请求数据
request('网址或者文件',(err,res,body)=>{ //res 请求到的对象，body 请求到的数据
    //使用cheerio处理请求到的数据
    const $=cheerio.load(body);
    //然后就可以像使用jquery一样获取各种所需的数据，如获取img标签的src属性
    console.log($('img').attr('src'));
})
```
