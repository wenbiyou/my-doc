## 是什么?
- Vuex是专为Vue应用程序开发的状态管理模式，在组件外集中存储、管理组件的状态
- 状态是响应式的，只能通过提交mutations才能改变状态
- Components ->  Actions -> Mutations -> State -> Compoments

## 核心概念
- state -> this.$store.state -> mapState
- getters -> this.$store.getters -> mapGetters
- mutations -> this.$store.commit() -> mapMutations
- actions -> this.$store.dispatch() -> mapActions

## 表单处理
```html
<!-- <input :value="message" @input="updateInputMesssage" /> -->

<input v-model="message" />

```

```js
computed: {
  // ...mapState({
  //   message: state => state.message
  // }),
  message: {
    get() {
      return this.$store.state.message
    },
    set(val) {
      this.$store.commit("updateMessage", value)
    }
  }
},
methods: {
  updateInputMesssage(e) {
    this.$store.commit("updateMessage", e.target.value)
  }

}


```