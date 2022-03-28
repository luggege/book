### computed与watch的区别

computed：**业务逻辑处理**，根据页面中某个值的变化而变化，做一些数据处理过滤。另外，也可以通过函数改变，但是computed只在数据**属性变化时**重新计算，computed会把值**缓存**起来供下次使用。

methods：函数**每次**调用都会执行

watch：**数据监听**，监听页面中某个特定状态的变化，监听的对象或变量必须在**data**里面声明，也可以监听**路由**的变化

```js
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
  <p>fullname: "{{ fullname }}"</p>
</div>
```

```js
var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'，
    user: {
      id: '001'
    }
  },
  // 计算属性
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }，
  // 数据监听
  watch:{
    message:function(newVal, oldVal){
        this.fullname = this.lastname + " " + this.firstname
    }
    user: {
      handler: function(newVal, oldVal){
        console.log(oldVal.id)
      }，
      deep: true  // 深度监听 对象中的属性发生改变
    },
    '$route.path': function (newVal, oldVal) {
       if (newVal !== oldVal) {
          console.log('路由变化');
       }
    },
    $route( to , from ){   
      console.log( to , from )
      // to , from 分别表示从哪跳转到哪，都是一个对象
      // to.path  ( 表示的是要跳转到的路由的地址 eg: /home );
   }
})
```

#### v-for与v-if

v-for不能与v-if同时使用，因为v-for比v-if优先级高，每v-for一次就会执行一次v-if，会引起性能问题

