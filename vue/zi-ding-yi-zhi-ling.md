#### 局部自定义指令

```js
directives: {
      // 指令名称
      focus: {
          // 被绑定元素插入父节点时调用
          inserted: el => {
              // 当前使用指令对DOM
              console.log(el);
              el.focus()
          },
          // 被绑定到元素上时调用
          bind: (el, binding) => {
              // el: 当前元素
              // binding：{name: focus, rowName: v-focus}
          },
          // 被绑定自定义指令的元素的值发生变化的时候调用
          update: () => {},
          // 被绑定的自定义指令没有绑定到元素上时调用
          unbind: () => {}
      }
  },
```

#### 全局自定义指令

```js
Vue.directive('focus', {
  inserted: el => {
    el.focus()  
  }
})

//简写
Vue.directive('focus', (el, binding) => {
  // 相当于调用 bind 和 update
})
```

#### 使用

```js
<input v-focus type="text">
```



