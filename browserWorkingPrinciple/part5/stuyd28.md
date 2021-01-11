## 阻碍前端组件化的因素
- CSS的全局属性会阻碍组件化
- DOM也是阻碍组件化的一个因素

## WebComponent 组件化开发
- 使用template属性来创建模板
- 创建一个类如：GeekBang
  - 查找模板内容
  - 创建影子DOM
  - 将模板添加到影子DOM上


## 浏览器如何实现影子DOM
- 影子DOM中的元素对于整个网页是不可见的
- 影子DOM的CSS不会影响整个网页CSSOM,影子DOM内部的CSS只对内部的元素起作用