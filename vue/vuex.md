### Vuex

> 是一个专为Vue.js应用程序开发的**状态管理模式**

#### 数据丢失问题

vuex的数据是保存在**运行内存**中的，当页面刷新的时候，会重新加载vue实例，vuex里面的数据就会重新初始化重新赋值，所以值会丢失，一般借助sessionStorage和localStorage、cookie来解决这个问题

* vuex的数据直接保存在sessionStorage和localStorage、cookie。例如：token保存在cookie中
* 再次请求远程数据，动态刷新vuex数据。例如菜单信息
* 页面刷新前，将vuex的数据保存在缓存中

#### 状态管理模式

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

#### ![](/assets/屏幕快照 2020-02-25 下午11.03.18.png)



