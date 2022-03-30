### vue ui出现cannot set property ‘context’ of null
npm版本过低，安装更高版本的npm
npm --version可以查看版本
npm install -g npm安装最新版本

### 如果不小心把终端终止了，可视化面板会显示已断开连接，可以重新在终端输入vue-ui
### vue-router
在vue2项目中，只能安装并使用3.x的vue-router，版本3和4的主要区别是创建路由的方式不同
4.x
```
```
3.x
在src-components目录下，创建需要使用路由切换的组件
src-router/index.js创建路由模块
在main.js中导入路由模块，并通过router属性进行挂载
```javaScript
import router from './router'
new Vue({
  render:h=> h(App),
  //挂载路由
  router
})
```
```

```