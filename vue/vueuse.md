### Vue.use\(plugin, arguments\)

#### plugin\(Function \| Object\)

插件的两种方式：

* 一种是**对象**，但是必须有一个**install**函数
* 一种是直接是**函数**暴露给Vue，当作install直接执行

源码分析：先看这个组件是否注册过（不允许重复注册），注册过就直接返回this（Vue对象）。否则就看如果是对象，调用install方法，通过apply改变this为该组件并传参arguments；如果是函数，就直接调用，此时的this为null

