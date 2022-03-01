### Vue.set\(\)

作用：

* 给对象添加响应式属性
* 更新数组

```js
var vm = new Vue({
  data: {
    a: 1,      // 因为vue实例化的时候，data里的数据才能getter/setter转换化
    arr: [1, 2, 3]
  }
})
// `vm.a` 现在是响应式的

vm.b = 2
// `vm.b` 不是响应式的

// vm.arr[1] = 'G'  // 不是响应式的
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

```js
// 通过索引修改数组、修改数组长度，vue是不能检测到的，所以不能更新视图
// 其他修改数组的方式
1.set
Vue.set(vm.arr, 1, 'w')

2.splice
vm.arr.splice(1, 1, 'q')

3.
vm.arr[1] = 'G' 
vm.$forceUpdate()

4.???
vm.arr[1] = 'O' 
vm.arr = [...vm.arr[1]]
```



