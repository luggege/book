### Vuex安装及使用

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

#### 组成部分

* state：存放共享数据
* mutation：定义方法修改state的值（同步：如果非同步，状态的改变将无法追踪）
* actions：通过dispatch分发actions（异步），通过commit提交mutation更改状态
* getters：类似于vue的计算属性，用来过滤一些数据（达到抽取通用方法的目的）
* modules：分模块管理

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
        todos: [
            {id: 1, text: '...', done: true},
            {id: 2, text: '...', done: false}
        ]
    },
    mutations: {
        change(state) {
            state.count++
        },
        SET_TOKEN: (state, data) => {
          state.token = data
        },
    },
    actions: {
        setToken: ({commit, dispatch}, data) {
            commit('SET_TOKEN', response.data.token)
        }
    },
    getters: {
        doneTodos (state) {
            return state.todos.fiter(todo => todo.done)
        }
    },
    modules: {
        moduleA,
        moduleB,
        ...
    }
})

console.log(store.state.count)   // 1

// 1. commit修改
store.commit('change')

// 2. 直接修改（多人协作容易出现问题，可开启严格模式）
store.state.count = 2          // console.log(store.state.count)   // 2

// 3. dispatch分发
store.dispatch('setToken', 'token...')

// getters 的使用
store.getters.doneTodos // [{id: 1, text: '...', done: true}]
```



