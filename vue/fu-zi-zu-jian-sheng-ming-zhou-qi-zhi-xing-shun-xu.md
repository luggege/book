### 父子组件生命周期执行顺序

* 无论 **v-if** 或 **v-show** 在父组件的默认值为true或**mounted**生命周期**之前**改变值为true，执行顺序都如下图所示：

![](/assets/beforeMount.png)

* **v-show** 在父组件的**mounted**期间改为true，执行顺序如下图所示：

![](/assets/v-show-mounted.png)

* **v-if **在父组件的**mounted**期间改为true，执行顺序如下图所示：

![](/assets/v-if-mounted.png)

结论：

* 只有在mounted周期内的变化才会触发update的
* 用v-if控制子组件是否渲染



