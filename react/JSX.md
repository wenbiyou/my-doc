## JSX是什么
- JSX 是 JavaScript 的一种语法扩展，它和模板语言很接近，但是它充分具备 JavaScript 的能力
- javascript -> babel -> React.createElement 这个javaScript的语法糖

## JSX如何映射为DOM
- JSX -> React.createElement(type, config, children) -> ReactElement -> 虚拟DOM -> ReactDOM.render() -> 真实DOM

- React.createElement 把除ref,self,key,source这四个属性外的属性，组装在props内


## 虚拟DOM是什么
- 虚拟DOM是JS对象
- 虚拟DOM是对真实DOM的描述
- 挂载阶段/更新阶段

## 虚拟DOM
组件初始化 -> render() -> 生成虚拟DOM -> ReactDOM.render() -> 真实DOM
组价更新 -> render() -> 生成虚拟DOM -> diff算法 -> 定位出两次虚拟DOM的差异

## 为什么需要虚拟DOM
- 原生js操作dom -> jquery操作dom -> 早期模板引擎方案（与jquery共存） -> 虚拟dom

- 虚拟DOM是前端开发为了追求更好的研发体验/研发效率的同时，仍保持还不错的的性能。

- 新旧虚拟dom树 -> diff -> 确定需要更新的内容 -> patch -> 真实dom(实现差量更新)

- 虚拟dom更高的js计算耗时，可能比较少的dom操作，批量更新

- 解决的问题：
  - 研发体验/研发效率的问题
  - 跨平台问题，让编码一次，多端允许提供可能




