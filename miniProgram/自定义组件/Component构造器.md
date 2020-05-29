## Component构造器

- 可指定组件的属性、数据、方法
- 可使用Component 构造器构造页面

```js
Component({
  behaviors: [],
  properties: {
    myProp1: String,
    myProp2: {
      type: String,
      value: 'hello'
    }
  },
  data: {}, // 私有数据
  lifetimes: {

  },
  methods: {

  }
})

```