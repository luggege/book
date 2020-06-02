### v-model：语法糖

* text、textarea：使用 **value **属性和 **input **事件

```js
 // <input type="text" v-model="value">

 <input type="text" v-bind:value="value" v-on:input="value = $event.target.value">

 <input type="textarea" v-bind:value="value" v-on:input="value = $event.target.value">

 <p>input的值为：{{value}}</p>
```

* radio、checkbox：使用 **checked **属性和 **change **事件
* * radio：绑定到选中的值

```js
// <input type="radio" name="person" value="男" v-model="checked">
// <input type="radio" name="person" value="女" v-model="checked">

<input type="radio" name="person" value="男" v-bind:checked="true" v-on:change="checked = $event.target.value">
<input type="radio" name="person" value="女" v-bind:checked="true" v-on:change="checked = $event.target.value">

<div>输入的input值为：{{checked}}</div>  // 选中的value值

<script>
export default {
    data(){
        return {
            checked: '女',
        }
    }
}
</script>
```

* * 单个复选框，绑定到**布尔值**

```js
<input type="checkbox" id="checkbox1" name="person" v-model="bool">
<label for="checkbox1">男</label>

<div>输入的input值为：{{bool}}</div>  // true / false
```

* * 多个复选框，绑定到选中的**数组**

```js
<input type="checkbox" id="checkbox1" name="person" value="男" v-model="names">
<label for="checkbox1">男</label>

<input type="checkbox" id="checkbox2" name="person" value="女" v-model="names">
<label for="checkbox2">女</label>

<div>输入的input值为：{{names}}</div>  // [ "男", "女" ]
```

* slect

```js
<select v-model="value" multiple>
    <option value="">请选择</option>
    <option value="A">A</option>
    <option value="B">B</option>
    <option value="C">C</option>
</select>

value: '', // []
```



