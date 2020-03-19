### computed与watch的区别

computed：**业务逻辑处理**，根据页面中某个值的变化而变化，做一些数据处理过滤。另外，也可以通过函数改变，但是computed只在数据**属性变化时**重新计算，函数**每次**都会去重新计算；computed会把**值缓存**起来供下次使用。

watch：**数据监听**，监听页面中某个特定状态的变化，监听的对象或变量必须在data里面声明

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
    }
})
```



