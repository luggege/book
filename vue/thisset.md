```js
var vm = new Vue({
  data: {
    a: 1
  }
})
// `vm.a` 现在是响应式的

vm.b = 2
// `vm.b` 不是响应式的
```

> vue不允许动态的添加根级别的响应式属性，但是可以使用Vue.set\(object, propertyName, value\)方法向嵌套对象添加响应式属性

```js
var vm = new Vue({
  data: {
    userProfile: {
      name: 'Anika'
    }
  }
})

Vue.set(vm.userProfile, 'age', 27)

// 或者
vm.$set(vm.userProfile, 'age', 27)
```



