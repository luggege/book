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
          }
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
```

#### 使用

```js
<input v-focus type="text">
```



