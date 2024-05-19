### 修改state的三种方式

1. 通过this.$store.state.xxx = xxx的方式直接修改
2. 通过this.$store.dispatch\('action方法名', 值\)的方式修改
3. 通过this.$store.commit\('mutation方法名', 值/对象\)的方式修改 `this.$store.commit({type: 'mutation方法名', data: 10})`

#### **三种方法的异同点**

* 相同点
* * 都能成功修改state的值，且是响应式的
* 不同点
* * 如果开启严格模式，直接修改state的值，控制台会报错
  * dispatch的方式含有**异步**操作，如请求接口
  * commit的方式是**同步**操作，否则不可追踪

#### **总结**

* 最好通过2、3的commit方式修改state的值，这样在vue的调试工具中能够追踪到每次state的变化，便于调试



