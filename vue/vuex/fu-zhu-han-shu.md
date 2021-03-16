### 四种辅助函数

* mapState:：返回一个对象，使用辅助函数生成计算属性，减少代码量

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


    // 2. 同名时数组方式（当计算属性的名称与state的子节点的名称一致时），可以简写如下：
    computed: mapState(['count'])


    // 3. 扩展运算符混合方式（与局部计算属性混合使用）
    computed: {
      localComputed(){},
      ...mapState()
    }
}
```

* mapGetters：仅仅是将store中的getter映射到局部计算属性

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

* mapMutations：将组件中的method映射为this.$store.commit\(\)调用

```js
import { mapMutations } from 'vuex'

export default {
    method: {
        // 把"this.add()"映射为“this.$store.commit('increment')”
        ...mapMutations(['increment'])

        // 或者
        ...mapMutations({
            add: 'increment'
        })
    }
}
```

* mapActions：将组件中的method映射为this.$store.dispath\(\)调用

```js
import { mapActions } from 'vuex'

export default {
    method: {
        // 把"this.add()"映射为“this.$store.dispath('increment')”
        ...mapActions(['increment'])

        // 或者
        ...mapActions({
            add: 'increment'
        })
    }
}
```



