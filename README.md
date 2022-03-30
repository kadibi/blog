# Headline

> An awesome project.


THis is just for test
```javascript {.line-numbers}
const express = require('express')//导入express模块
const router = express.Router() //创建路由对象
router.get('/user/list',(req,res)=>{
    res.send('get user list')//挂载获取用户信息的路由
})
router.post('/user/add',(req,res)=>{
    res.send('add user list')//挂载添加用户信息的路由
})
module.exports = router   //向外导出路由 
```
