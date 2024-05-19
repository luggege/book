### 四种辅助函数

* mapState:：**返回一个对象**，当一个组件需要获取多个状态的时候，使用辅助函数生成**计算属性**，减少代码量

```js
import { mapState } from 'vuex'

export default {
    //1. 对象方式
    computed: mapState({
        // 1. 箭头函数
        count: state => state.count

        // 2. 字符串，等同于state => state.count
        count: 'count'

        // 3. 使用常规函数，保证this获取局部状态
        count() {
            return state.count + this.localCount
        }
    })


    // 2. 同名时数组方式（当计算属性的名称与state的子节点的名称一致时，即 this.count 为 store.state.count），可以简写如下：
    computed: mapState(['count'])


    // 3. 扩展运算符混合方式（与局部计算属性混合使用）
    computed: {
      localComputed(){},
      ...mapState({})
    }
}
```

* mapGetters：仅仅是将store中的getter映射到局部**计算属性**

```js
import { mapGetters } from 'vuex'

export default {
    computed: {
        ...mapGetters(['count'])

        // 或者--->把"this.newCount"映射为“this.$store.getters.count”
        ...mapGetters({
            newCount: 'count'
        })
    }
}
```

* mapMutations：将组件中的**methods**映射为this.$store.commit\(\)调用

```js
import { mapMutations } from 'vuex'

export default {
    methods: {
        // 将"this.increment()"映射为“this.$store.commit('increment')”
        ...mapMutations(['increment'])

        // 或者 将"this.add()"映射为“this.$store.commit('increment')”
        ...mapMutations({
            add: 'increment'
        })
    }
}
```

* mapActions：将组件中的**methods**映射为this.$store.dispath\(\)调用

```js
import { mapActions } from 'vuex'

export default {
    methods: {
        // 将"this.increment()"映射为“this.$store.dispath('increment')”
        ...mapActions(['increment'])

        // 或者 将"this.add()"映射为“this.$store.dispath('increment')”
        ...mapActions({
            add: 'increment'
        })
    }
}
```

```js
// store.dispatch 可以处理被触发的 action 的处理函数返回的 Promise，并且 dispatch 仍旧返回 Promise
actions: {
    actionA({commit, disptach}, data) {
        return new Promise((res, rej) => {
            setTimeout(() => {
                console.log('aaaa')
            }, 1000)
        })
    },
    async actionB({commit, dispatch}, data) {
        await dispatch('actionA')
        console.log('bbbb')
    }
}
```



