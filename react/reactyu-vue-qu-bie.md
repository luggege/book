### React与Vue的区别

* React全部用js来处理，所以有了jsx；vue是把html、js、css写在一块
* React整体思路就是函数式，所以推崇纯组件；Vue使用template模版，就有模版语法、模版指令概念，如：v-for、@click
* React是类式写法 API少，vue是申明式组件 API很多（vue3.0是类式写法）

* React：单向数据流；Vue：响应式，基于数据可变，对每一个属性建立watcher来监听，当属性变化，响应式更新对应的虚拟dom，所以当state特别多的时候，watcher也特别多，会导致卡顿，所以大型项目一般用react，更加可控

* React做的事情很少，很多都交给社区去做；

* vue很多东西都是内置的 Vue追求开发简单；React更在乎是否正确



