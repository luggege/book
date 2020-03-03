### computed与watch的区别

computed：根据页面中某个值的变化而变化，做一些数据处理过滤。另外，也可以通过函数改变，但是computed只在数据变化时重新计算，函数每次都会去重新计算

watch：监听页面中某个特定状态的变化，监听的对象或变量必须在data里面声明

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
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }，
  watch:{
    message:function(newVal, oldVal){
        this.fullname = this.lastname + " " + this.firstname
    }

})
```



