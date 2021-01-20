## 栈溢出
- 全局执行上下文
- 函数执行上下文
- 是eval函数，也会生成执行上下文

## 栈
- 类似于一端被堵住的单行线
- 栈中的元素满足后进先出的特点

## 调用栈
- 定义：把这种用来管理执行上下文的栈称为执行上下文栈，又称为调用栈。


## 总结
- 每调用一个函数，javaScript会为其创建一个执行上下文，并把该执行上下文压入调用栈，然后javaScript引擎开始执行代码
- 一个函数A调用函数B,javaScript会为函数B创建执行上下文，并把函数B执行上下文压入栈顶
- 当前函数执行完毕，javaScipt引擎会把该函数的执行上下文弹出栈
- 当分配的调用栈空间被占满时，会发生堆栈溢出问题
- 栈是一种重要的数据结构