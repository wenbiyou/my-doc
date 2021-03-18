## 起步
- 将组件映射到路由，并告诉vue-router在哪里渲染他们
- this.$router 访问路由器
- this.$route  访问当前路由

## 动态路由
- 路由参数使用:标记，
- this.$route.params、this.$route.query、this.$route.hash

## 嵌套路由
- 空的子路由

## 编程式导航
- this.$router.push()、this.$router.replace()、this.$router.go()
- push和replace很像，push会向history添加新记录，replace替换当前记录

```js
this.$router.push("user")
this.$router.push({name: "user",, params: {id: 123}})
this.$router.push({path: "/user"})
this.$router.push({path: "/user",, query: {id: 123}})


this.$router.replace("user")
this.$router.replace({path: "/user", query: {id: 123}})


this.$router.go(-1)

```

## 重定向&别名
- redirect
- alias  (''|string|[])

## H5 history模式
- 利用history.pushState 完成URL跳转无须重新加载页面
- 需服务端进行配置

## 导航守卫
- 全局的  beforeEach((to, from, next)), afterEach((to, from)), beforeResolve((to, from, next))
- 路由的  beforeEnter: function(to, from, next) {}
- 组件的  beforeRouteEnter(to, from, next) {}, beforeRouteUpdate(to, from, next) {}, beforeRouteLeave(to, from, next) {}

- beforeRouteEnter 通过回调给next访问组件实例，可用于在导航完成前获取数据

## 数据获取
- 导航完成后获取数据
- 导航完成前获取数据 通过beforeRouteEnter的next实现

## 路由懒加载
- 路由被访问时才加载对应组件， const Foo = () => import('./Foo.vue')
- 路由按组进行分块
```js

const Foo1 = () => import(/* webpackChunkName: 'Foo'  */'./Foo1.vue')
const Foo2 = () => import(/* webpackChunkName: 'Foo'  */'./Foo2.vue')
const Foo3 = () => import(/* webpackChunkName: 'Foo'  */'./Foo3.vue')
const Foo4 = () => import(/* webpackChunkName: 'Foo'  */'./Foo4.vue')

```
