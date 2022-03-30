## 路径参数和查询参数
### 路径参数params
跟在URL路径后面的是params参数，可以动态绑定，有这个的路由叫做动态路由
#### 获取方式
- props获取
- 在路由参数对象上通过this.$route.parmas获取
#### params传参问题
1. 如何指定params参数可传可不传
```javaScript
  // 如果路由path要求传递params参数,但是没有传递,会发现地址栏URL有问题，详情如下：
  // Search路由项的path已经指定要传一个keyword的params参数，如下所示：
  path: "/search/:keyword",
  // 执行下面进行路由跳转的代码：
  this.$router.push({name:"Search",query:{keyword:this.keyword}})
  // 当前跳转代码没有传递params参数
  // 地址栏信息：http://localhost:8080/#/?keyword=asd
  // 此时的地址信息少了/search
  // 正常的地址栏信息: http://localhost:8080/#/search?keyword=asd
  // 解决方法：可以通过改变path来指定params参数可传可不传 
  path: "/search/:keyword?",//?表示该参数可传可不传
```
2. 由（1）可知params可传可不传，但是如果传递的时空串，如何解决 
```javaScript
 this.$router.push({name:"Search",query:{keyword:this.keyword},params:{keyword:''}})
//  出现的问题和1中的问题相同,地址信息少了/search
//  解决方法： 加入||undefined，当我们传递的参数为空串时地址栏url也可以保持正常
 this.$router.push({name:"Search",query:{keyword:this.keyword},params:{keyword:''||undefined}})
```
3. params参数可以通过props传
#### 传参方式
- 字符串形式
```
this.$router.push("/search/"+this.params传参+"?k="+this.query传参)
```
- 模板字符串
```
this.$router.push("/search/+router.push("/search/+{this.params传参}?k=${this.query传参}")
```

- 对象（常用）
```javaScript
this.$router.push({name:“路由名字”,params:{传参},query:{传参})。
// 以对象方式传参时，如果我们传参中使用了params，只能使用name，不能使用path，如果只是使用query传参，可以使用path  
```
### 查询参数query
？后面的参数,