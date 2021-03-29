Action
  - dispatch()
  - action函数

reducer(state, action)
  - reducer是一个纯函数，仅用于计算下一个state,是完全可以预测的
  - reducer拆分
  - combineReducer() 将多个子reduer合并成根reducer
store
  - 维持应用的state
  - 提供getState() 获取state
  - 提供dispatch(action) 更改state
  - 通过subscribe(listener) 注册一个监听函数
  - 通过subscribe(listener) 返回的函数注销监听器
  - Redux应用只有一个单一的store
Usage with React
  - 展示组件
    - propTypes
    - props => 属性和方法
  - 容器组件
    - 容器组件把展示组件连接到Redux
    - 技术上，容器组件通过store.subscribe()监听器把Redux状态树的部分状态通过 props 传递给要渲染的组件
    - connect()(展示组件)  connect自身带有react的性能优化，建议使用connect
  - 其他组件
  - 传入Store
    - <Provider store={store}></Provider>

-----

## Flux架构
View
Action
Dispatcher
Store

Action -> Dispatcher -> Store -> View -> Action -> Dispatch -> ...
严格的单向数据流  -> 状态变化可预测 -> 从根本上避免了混乱的数据关系

## Redux
Redux 是javaScript状态容器，它提供可预测的状态管理


设计思想与Flux一脉相承
Store
Action
Reducer 

Action -> Reducer -> Store -> View -> Action

任何组件都可以通过约定的方式从Store读取全局的状态
任何组件都可以通过合理派发Action来修改全局状态

## createStore
是redux最先调用的方法，是整个流程的入口，也是Redux最核心的Api

createStore(reducer, preloadedState, enhancer)

- getState
- subscribe
- dispatch

## Redux工作流的核心：dispatch动作

- dispatch 刚好把action、reducer、store这三位主角给串联起来了

调用dispatch,入参为action -> 前置校验 -> "上锁"：将isDispatching设置为true -> 调用reducer，计算新的state -> "解锁"：将isDispatching设置为false -> 触发订阅 -> 返回action


- 通过"上锁 "避免"套娃式"的 dispatch
- 触发订阅的过程

## redux中的 “发布-订阅”模式： 认识subscribe
- 只有在监听状态变化时，才会调用subscribe

- subscribe 是如何与 Redux 主流程结合的呢？
在store对象创建成功后，通过调用store.subscribe 来注册监听函数，也可以调用 store.subscribe 函数的返回值来取消监听函数, 监听函数用listener数组来维护。当dispatch 发生时，Redux会在reducer执行完毕后，将listeners数组中的监听函数逐一执行。

store -> store.subscribe -> listener -> dispatch -> reducer -> 逐一执行listeners中监听函数

## 中间件
- 使用中间间来增强createStore,如在redux中引入异步数据
- redux-thunk -> 经典的异步Action解决方案

action -> middleware -> dispatch -> reducer -> nextState

applyMiddleware 改写dispatch的校验

- 执行时机: action分发之后，reducer触发之前
- applyMiddleware会对dispatch函数进行改写，使得dispatch触发reducer之前，会首先执行对redux中间间的链式调用



