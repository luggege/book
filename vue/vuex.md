# Vuex

> 是一个专为Vue.js应用程序开发的**状态管理模式**

### 状态管理模式

```js
new Vue({
    // state
    data() {
        return {
            count: 0;
        }
    },
    // view
    template: `
        <div>{{ count }}</div>
    `,
    // actions
    methods: {
        increment() {
            this.count++
        }
    }
})
```

* state：驱动应用的数据源
* view：以声明方式将state映射到视图
* actions：相应在view上的用户输入导致的状态变化

但是，当我们的应用遇到多个组件共享状态时，单向数据流的简洁性很容易被破坏：

* 多个视图依赖于同一状态（继承）
* 来自不同视图的行为需要改变同一状态（修改）

因此，把组件的共享状态抽取出来，以一个全局单例模式管理

![](/assets/屏幕快照 2020-02-25 下午11.03.18.png)

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
store.commit('change')
console.log(store.state.count)   // 2


store.dispatch('GetUserInfo')
```

* state：存放共享数据
* mutation：定义方法修改state的值
* actions：通过dispatch分发actions，通过commit异步处理数据
* getters：类似于vue的计算属性，用来过滤一些数据
* modules：分模块管理



