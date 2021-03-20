- react是用Js构建快速响应的大型web应用程序开发的首选

## Stack Reconciler
- javaScipt对主线程的超时占用问题
- Stack Reconciler是一个同步递归的过程
- 栈调和机制下的Diff算法，其实是树的深度优先遍历的过程
- 这个过程的致命在于它是同步的，不可以被打断  Stack Reconclier 需要的调和时间会很长

- Reconciler(找不同) -> Rendeerer(渲染不同)


## 什么Fiber
- 纤程
- 实现增量渲染

## 增量渲染
- 可中断、可恢复与优先级

- Scheduler(调度更新的优先级) -> Reconciler(找不同) -> Rendeerer(渲染不同)

