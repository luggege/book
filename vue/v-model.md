v-model：语法糖

```js
 // <input type="text" v-model="value">
 // 等价于
 <input type="text" v-bind:value="value" v-on:input="value = $event.target.value">
 <p>input的值为：{{value}}</p>
```



