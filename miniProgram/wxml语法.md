## 数据绑定
- 使用 {{}}
- 组件属性、控制属性、关键字需在双引号内
  ```html
  <view id="item-{{id}}"></view>
  <view wx;If="{{condition}}"></view>
  <checkbox checked="{{false}}"></checkbox>
  ```
- 可在{{}}内进行简单运算
```html
<view hidden="{{flag ? true : false}}">Hidden</view>
<view>{{a + b}} + {{c}} + d</view>
<view wx:if="{{length > 5}}"></view>
<view>{{"hello" + name}}</view>
<view wx:for="{{[a, 1, 2, 3, 4]}}">{{item}}</view>
```

- 对象 （任意组合键值对数据对象）


## 列表渲染
- wx:for  当前项下标默认index, 当前项变量名默认item
- wx:for-item 指定当前项变量名
- wx:for-index 指定当前项下标变量名
- 使用block 渲染一个包含多个节点的结构块
  ```html
  <block wx:for="{{[1, 2, 3]}}">
    <view>{{index}}</view>
    <view>{{item}}</view>
  </block>
  ```
- wx:key 指定列表项目的唯一标识符
  * 字符串，item的某个唯一属性且不能动态改变
  * 保留关键字 *this 代表for循环中item本身，这种表示item本身时一个唯一的字符串或数字
- 花括号和引号之间如有空格，将最终被解析为字符串
```html
<view wx:for="{{[1, 2, 3]}} ">{{item}}</view>
 等同于
<view wx:for="{{[1, 2, 3] + ' '}}">{{item}}</view>
```

## 条件渲染
- wx:if,wx:elif,wx:else
- 一次判断多个组件标签，可用<block />包装
  ```html
  <block wx:if="{{true}}">
    <view>1</view>
    <view>2</view>
  </block>
  ```
- block 不是一个组件，仅是一个包装元素，不会在页面做任何渲染，只接受控制属性
- wx:if vs hidden
  * wx:if 是惰性的，hidden始终会被渲染
  * wx:if 有更高的切换消耗，不怎么变化的使用wx:if
  * hidden 有更高的初始渲染消耗，频繁切换使用hidden好

## 模板
- 在模块中定义代码片段，然后再不同的地方调用
- 定义模板 [name]
  ```html
  <template name="msgItem">
    <view>
      <text>{{index}}: {{msg}}</text>
      <text>Time: {{time}}</text>
    </view>
  </template>
  ```
- 使用模板 [is]
```html
<template is="msgItem" data="{{...item}}"></template>
```

- 模板的作用域
  * 模板拥有自己的作用域，只能使用data传入的数据以及模板定义文件中定义的 <wxs /> 模板

## 引用
- wxml 提供了两种文件引用方式 import 和 include
- import
  * 可在改文件中使用目标问搭建定义的template
  * import有作用域的概念
- include
  * 可将目标文件除了 <template /> <wxs /> 外的整个代码引入






