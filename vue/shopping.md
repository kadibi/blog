### find和filter的区别
find找到数组中符合条件的第一项，并返回查到的那一项，不是数组，并且不改变原数组
```javaScript
    let arr = [{ name: '老于', age: 18 }, { name: '张三', age: 15 }, { name: '李四', age: 22 }, { name: '王五', age: 25 }, { name: '老朱', age: 12 }]
    let str=''
    str=arr.find(item=>{
      return item.age>12
    })
    console.log(arr);
    console.log(str);//{ name: '老于', age: 18 }
```
filter找到数组中符合条件的并且返回一个数组，也不改变原数组
```javaScript
    let arr = [{ name: '老于', age: 18 }, { name: '张三', age: 15 }, { name: '李四', age: 22 }, { name: '王五', age: 25 }, { name: '老朱', age: 12 }]
    let arr1 = []
    arr1 = arr.filter(item => {
      return item.age > 12
    })
    console.log(arr);
    console.log(arr1);//[{ name: '老于', age: 18 }, { name: '张三', age: 15 }, { name: '李四', age: 22 }, { name: '王五', age: 25 }]
```
### props里面数据是只读，data里面的可读可写
想要改props里面的数据需要自定事件告诉传这个数据的父组件，案例中的input双向绑定数据不能绑props里面的，可以巧妙地将props数据的初始值转存在data里面
```html
 <!-- 输入框 -->
    <input
      type="number"
      class="form-control form-control-sm iptnum"
      v-model.number.lazy="number"
    />
```
```javaScript
props: {
    num: {
      type: Number,
      default: 0,
    },
  },
  data() {
    return {
      //拿到的是props里面的初始值
      number: this.num,
    }
  },
```