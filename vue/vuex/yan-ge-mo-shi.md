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

* 严格模式下，通过this.$store.state.xxx = xxx直接修改state的值会报错（状态变更**不是由mutation函数引起**的），这能保证所有的状态变更都能被调试工具追踪到

* 如果：严格模式下：obj是计算属性中返回的一个属于vuex的对象，在用户输入时，v-model会试图直接修改obj.message，由于这个修改不是mutation函数中执行的，所以会报错 `<input v-model="obj.message">`两个解决方案：
* 1. 用vue的思维模拟v-model 
  2. ```js
     <input :value="message" @input="updateMessage">


     computed: {
         ...mapState({
             message: state => state.obj.message
         })
     }

     methods: {
         updateMessage(e) {
             this.$store.commit('updateMessage', e.target.value)
         }
     }

     // store中的mutation函数
     state: {
         obj: {
             message: ''
         }
     }
     mutations: {
         updateMessage(state, data) {
             state.obj.message = data
         }
     } 
     ```
    2. 使用setter的双向绑定计算属性
    ```js
    <input :value="message">
    
    computed: {
        message: {
            get() {
               return this.$store.state.obj.message 
            },
            set(value) {
                this.$store.commit('updateMessage', value)
            }
        }
    }
    
    // store中的mutation函数
     state: {
         obj: {
             message: ''
         }
     }
     mutations: {
         updateMessage(state, data) {
             state.obj.message = data
         }
     } 
    ```



