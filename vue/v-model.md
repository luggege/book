v-model：语法糖

* text、textarea：使用value属性和input事件

```js
 // <input type="text" v-model="value">

 // 等价于
 <input type="text" v-bind:value="value" v-on:input="value = $event.target.value">

 <input type="textarea" v-bind:value="value" v-on:input="value = $event.target.value">

 <p>input的值为：{{value}}</p>
```

* radio、checkbox：使用checked属性和change事件

```js
<input type="radio" name="person" value="男" v-bind:checked="checked" v-on:change="change($event)">
<input type="radio" name="person" value="女" v-bind:checked="checked" v-on:change="change($event)">
```



