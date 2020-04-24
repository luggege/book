v-model：语法糖

* text、textarea：使用value属性和input事件

```js
 // <input type="text" v-model="value">

 <====>
 <input type="text" v-bind:value="value" v-on:input="value = $event.target.value">

 <input type="textarea" v-bind:value="value" v-on:input="value = $event.target.value">

 <p>input的值为：{{value}}</p>
```

* radio、checkbox：使用checked属性和change事件
* * radio

```js
<input type="radio" name="person" value="男" v-model="checked">
<input type="radio" name="person" value="女" v-model="checked">
<====>
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

* * 单个复选框，绑定到布尔值   

```js
<input type="checkbox" id="checkbox1" name="person" v-model="bool">
<label for="checkbox1">男</label>

<div>输入的input值为：{{bool}}</div>  // true/false
```

* * 多个复选框，绑定到选中的数组

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



