## nrm
nrm ( npm registry manager )：npm下载地址切换工具
### 使用步骤
1. 使用npm install nrm –g 下载它
2. 查询可用下载地址列表 nrm ls
3. 切换npm下载地址 nrm use 下载地址名称

## package.json文件的作用
项目描述文件，记录了当前项目信息，例如项目名称、版本、作者、github地址、当前项目依赖了哪些第三方模块等。
使用npm init -y命令生成。
## HTTP状态码
- 200 请求成功
- 404 请求的资源没有被找到
- 500 服务器端错误
- 400 客户端请求有语法错误

## express
express作用和内置的http模块类似，是专门用来创建web服务器的便捷方法
### 路由
路由是指客户端请求地址与服务器端程序代码的对应关系。简单的说，就是请求什么响应什么。(请求方式、URL、回调函数)
路由使用方法：推荐将路由单独抽离为单独的模块
1. 创建对应路由js文件
2. 调用express.Router()创建路由对象
3. 向路由对象上挂载具体的路由
4. 通过module.exports向外共享路由对象
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

5. 导入路由模块，通过app.use()注册路由模块
```
//导入路由模块
const userRouter = require('./Router')
//注册路由模块
app.use(userRouter)
//为路由模块统一添加前缀api
app.use('/api',userRouter)
```

app.use()这个函数的作用就是来注册全局中间件

### 中间件
给请求做预处理的函数
中间件函数的形参里面必须有next参数，而路由函数只有req和res参数
### 中间件的作用
多个中间件之间共享同一份req和res，可以在上游的req和res添加自定义属性和方法，供下游的中间件或者路由使用


# ajax

Ajax是 Asynchronous JavaScript and XML的缩写，意思是异步网络请求,Ajax带来的最大影响就是页面可以无刷新的请求数据
ajax运行环境
Ajax 技术需要运行在网站环境中才能生效，要能以localhost域名打开页面，要借助node开启一个网站服务器，并且实现静态资源访问功能，将代码写在html文件中，然后将html文件放在静态资源文件夹中，这样既可通过域名访问这个html文件。

实现一个ajax请求
```
var xhr = new XMLHttpRequest(); // 创建XMLHttpRequest对象
// 发送请求:
xhr.open('GET', '/api/categories');//初始化请求
xhr.setRequestHeader("Content-Type", "application/json") //设置请求头，就是send()里面内容的格式要求，get 请求是不能提交 json 对象数据格式的
xhr.responseType = 'json'//设置响应体数据的类型，可自动将服务器返回的json字符串转换为对象形式
xhr.send();//到这一步，请求才正式发出

//ajax是异步的，设置回调函数,事件绑定
xhr.onreadystatechange = function () { // 状态发生变化时，函数被回调
    if (xhr.readyState === 4) { // 成功完成
        // 判断响应状态码
        if (xhr.status === 200) {
            // 成功，通过responseText拿到响应的文本:
            return success(xhr.responseText);
        } else {
            // 失败，根据响应码判断失败原因:
            return fail(xhr.status);
        }
    } else {
        // HTTP请求还在继续...
    }
}

```
使用原生的js还是比较繁琐，实际工程中建议使用jQuery之类的库，封装的ajax请求方法非常好用
## jquery


## axios
axios 是一个基于Promise 用于浏览器和 nodejs 的 HTTP 客户端，本质上也是对原生XHR的封装，只不过它是Promise的实现版本，符合最新的ES规范，有以下特点：

从浏览器中创建 XMLHttpRequests
从 node.js 创建 http 请求
支持 Promise API
拦截请求和响应
转换请求数据和响应数据
取消请求
自动转换 JSON 数据
客户端支持防御 XSRF

