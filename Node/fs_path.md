# fs,path
```javascript
//引入模块
const fs=require('fs');
const path=require('path');
//读取文件
fs.readfile(path.join(__dirname,'文件名'),'编码格式 utf-8',(err,data)=>{ //data为读取到的数据
    if(err) throw err;
    console.log(data);
})
//写入文件
fs.writefile(path.join(__dirname,'文件名'),data,'编码格式 utf-8',err=>{ //data为要写入的数据
    if(err) throw err;
    console.log('写入成功');
})
//删除文件
fs.unlink(path.join(__dirname,'文件名'),err=>{ 
    if(err) throw err;
    console.log('删除成功');
})
//创建文件夹
fs.mkdir(path.join(__dirname,'文件夹名'),err=>{ 
    if(err) throw err;
    console.log('创建成功');
})
//删除文件夹
fs.rmdir(path.join(__dirname,'文件夹名'),err=>{ //文件夹必须为空
    if(err) throw err;
    console.log('删除成功');
})
```

