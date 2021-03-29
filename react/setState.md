

基于React15：setState是一个异步方法？还是同步更新？

## 异步的动机和原理 -> 批量更新的艺术
- setState -> 生命周期
- 避免频繁的re-render(较大的性能开销)
- setState & Vue/$nextTick
- 同一方法多次setState的合并并不是单纯的更新累加，对于相同的属性设置，React只为其保留最后一次更新


## 同步现象的背后，从源码角度看setState工作流
- setTimeout 帮助setState “逃脱了”React的异步监控

setState -> enqueueSetState -> enqueueUpdate -> batchingStrategy ()

## 理解React中的Transaction(事务)机制


## 同步现象的本质
isBatchingUpdates


## setState的表现会因调用场景的的不同从而表现不同
- 在react钩子函数及合成事件中，表现为异步
- 在setTimeout、setInterval等函数，包括DOM原生事件中，它表现为同步


## 使用
```js
- 只能在construction初始化时 this.state = {count: 1}
- 其他地方只能使用 setState({count: 2})
setState((state, props) => ({
  count: state.count + props.nums
}))
```
