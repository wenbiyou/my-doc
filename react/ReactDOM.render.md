# ReactDOM.render调用栈 -> 初始化阶段
- 渲染过程是同步的
- FiberNode
- performSyncWorkOnRoot是render阶段的起点
- render阶段的任务是完成Fiber树的构建，它是整个渲染链路中最核心的一环

- 模式：
legacy模式：
blocking模式：
concurrent模式：

mode属性决定着这个工作流是一气呵成（同步）的还是分片执行（异步）的


## 异步模式下的首次渲染链路
- concurrent模式

## Fiber架构一定是异步渲染吗
- Fiber的设计主要为了Concurrent而存在
- Fiber架构师同时兼容了同步渲染与异步渲染的设计

# ReactDOM.render调用栈 -> 渲染阶段
- ReactDOM.render 触发同步模式，仍是一个深度优先搜索的过程
- beginWork将创建新的Fiber节点，而completeWork则负责将Fiber节点映射为DOM节点
