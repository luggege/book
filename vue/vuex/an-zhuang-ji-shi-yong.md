## Vuex安装及使用

```javascript
<script src="/path/to/vue.js"></script>
<script src="/path/to/vuex.js"></script>
```

或者

```javascript
// 命令行执行
npm install vue 
npm install vuex
```

```javascript
// 项目中引入、安装
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

// 使用
const store = new Vuex.Store({
    state: {
        count: 1,
        token: '',
    },
    mutations: {
        change(state) {
            state.count++
        },
        SET_TOKEN: (state, token) => {
          state.token = token
        },
    },
    actions: {
        commit('SET_TOKEN', response.data.token)

    }
})

console.log(store.state.count)   // 1

// 1. commit修改
store.commit('change')

// 2. 直接修改（多人协作容易出现问题，可开启严格模式）
// store.state.count = 2
console.log(store.state.count)   // 2

// 3. dispatch分发
store.dispatch('SET_TOKEN')
```

* state：存放共享数据
* mutation：定义方法修改state的值
* actions：通过dispatch分发actions，通过commit异步处理数据
* getters：类似于vue的计算属性，用来过滤一些数据
* modules：分模块管理



