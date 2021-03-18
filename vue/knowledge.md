- MVvm模型 
- 响应式原理
- 渲染函数&JSX
- 模板编译原理
- v-if & v-show
- v-if & v-for
- v-for带key
- Vue组件是如何通信
- vue-router
- Vuex
- vue-cli

## MVvm模型
- model 模型（数据层）
  - 仅关注数据
- view  视图（用户操作界面）
  - viewModel对model更新，会通过数据绑定更新视图
- ViewModel 视图模型（绑定器）
  - viewModel中的双向数据绑定，当model发生改变，ViewModel会自动更新，从而改变视图

- 解决问题：简化了界面与业务的依赖，解决了数据频繁更新

- 问题： 
  - bug比较难调试，可能是model的问题，也可能是view的问题
  - 项目比较大时，数据绑定耗内存

- 实现方式：数据劫持，通过defineProperty(),Vue3使用proxy实现数据劫持
(react使用脏值检查实现双向数据绑定)

- Vue没有完全遵循MVVM模型，如$refs属性，违背了Vue数据驱动的思想


## 响应式原理
- Vue会遍历对象的属性，使用Object.defineProperty将property转为getter/setter,Vue能在内部追踪依赖。
- 每个Vue实例都对应一个Watcher实例，将这些property记录为依赖，当依赖项的setter触发时，会通知wather,从而使关联组件重新渲染

- Vue检测对象和数组
```js
this.$set(this.Obj, "b", 3)
this.someObj = Object.assign({}, this.someObj, {a: 1})

this.$set(this.ArrB, indexOfItem, newValue)
```

- 声明式property: 初始化时声明所有根级响应式属性

- 异步更新队列
Vue更新Dom是异步的，当数据发生改变时，Vue开启一个队列，并缓冲同一事件循环的所有数据更改，如果一个watcher被多次触发，只会加入队列一次。并在下一个事件循环'tick'中，Vue刷新队列并执行实际工作

Vue的异步队列先尝试使用Promise.then(), MutationObserver,SetImmediate,如果不支持则采用setTimeout(fn, 0)代替

## 渲染函数&JSX
- 需要JavaScript完全编译能力，可用渲染函数
- 节点、树以及虚拟DOM
- Vue通过建立虚拟DOM来追踪自己要如何改变真实DOM
- 虚拟节点 =》 VNode, VNode必须是唯一的
- render, createElement
- JSX 用更接近模板的语法写渲染函数
- 函数式组件
  - 无状态，无实例（没有this上下文）
  - functional: true

## 模板编译原理

- Template
  - 模板语法（HTML的扩展）
  - 数据绑定使用Mustache语法（双大括号）
  - 学习成本低，内置指令简化开发
- JSX
  - javaScript的语法扩展
  - 数据绑定使用单括号
  - 灵活

- Template、JSX都是语法糖，实际都被编译成了createElement渲染函数

## Vue组件是如何通信
- props + $emit
- Vuex
- 访问元素&组件
  - 访问子组件实例 $refs
  - 访问父组件实例 $parent
  - 访问根实例 $root
  - 依赖注入 provide/inject

## 程序化事件监听器
```js
mounted() {
  var Pikaday = new Pikaday({
    field: this.$refs.input,
    format: "YYYY-MM-DD"
  })

  this.$once('hook:beforeDestory', () => {
    Pikaday.destory()
  })

}
```

