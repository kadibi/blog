## submit可以监听表单的提交事件，要写在form标签中
```
    <form class="form-inline" @submit.prevent="onFromSubmit">
```
## this.$emit触发自定义事件传参数到父组件里面时，父组件里面定义的自定义事件不要传参
```html
//子组件
          this.$emit('add',this.taskname)
//父组件,onAddNewTask后面不要跟()，直接在methods里接
    <todo-input @add="onAddNewTask"></todo-input>
```
```javaScript
//methods
    onAddNewTask(taskname){
    this.todoList.push({
      id:this.nextId,
      task:taskname,
      done:false
    })
    this.nextId++
    },
```

