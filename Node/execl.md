# node-xlsx
```javascript
//引入模块
const excel = require('node-xlsx');
const fs = require('fs');
const path = require('path');
//创建xlsx表格的格式
    //设置第一行的表名,注意，execl数据为二维数组;
    let arr=[[
    'sid',
    'title',
    'descrip',
    'price',
    'typelist',
    'urls'
]];
    //设置xlsx的表数据
    let edata = [{
        name: 'sheet1',
        data: []
    }],buffer = null;
    //添加数据进表格
    arr.push([
        1,2,3,4,5,6,7
    ]);
    //将数据加入到表
    edata.data=arr;
    //生成xlsx数据格式
        buffer = excel.build([{
                name: 'sheet1',
                data: arr2
            }]);
    //写入到实际的xlsx文件
    fs.writeFile('./resul.xls', buffer, err => {
        if (err) throw err;
        console.log('写入成功');
    });
    // 读xlsx
    var obj = excel.parse("./" + "resul.xls");
    console.log(JSON.stringify(obj));
```