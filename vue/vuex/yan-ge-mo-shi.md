### 严格模式

* 创建store的时候，可通过传参开启严格模式（默认关闭严格模式）

```js
new Vuex.Store({
    strict: true,
    state: {

    },
    mutations: {

    },
    actions: {

    }
})
```

* 严格模式下，通过this.$store.state.xxx = xxx直接修改state的值会报错（状态变更不是由mutation函数引起的），这能保证所有的状态变更都能被调试工具追踪到



