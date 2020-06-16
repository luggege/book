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

<input type="radio" name="person" value="男" v-on:change="$event.target.checked ? value = $event.target.value : ''">
<input type="radio" name="person" value="女" v-on:change="$event.target.checked ? value = $event.target.value : ''">

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
// <input type="checkbox" id="checkbox1" name="person" v-model="bool">
// <label for="checkbox1">男</label>

<input type="checkbox" v-bind:checked="bool" v-on:change="bool= $event.target.checked">

<div>输入的input值为：{{bool}}</div>  // true / false

<script>
export default {
    data(){
        return {
            bool: false,
        }
    }
}
</script>
```

* * 多个复选框，绑定到选中的**数组**

```js
// <input type="checkbox" id="checkbox1" name="person" value="男" v-model="names">
// <label for="checkbox1">男</label>

// <input type="checkbox" id="checkbox2" name="person" value="女" v-model="names">
// <label for="checkbox2">女</label>

<input type="checkbox" value="男" v-on:change="$event.target.checked ? names.push($event.target.value) : names.splice(names.indexOf($event.target.value), 1)">
<input type="checkbox" value="女" v-on:change="$event.target.checked ? names.push($event.target.value) : names.splice(names.indexOf($event.target.value), 1)">

<div>输入的input值为：{{names}}</div>  // [ "男", "女" ]


<script>
export default {
    data(){
        return {
            names: [],
        }
    }
}
</script>
```

* slect：利用 **change **事件，单选时：绑定到选中的值，多选时：绑定到选中的数组

```js
// <select name="" id="" v-model="value">
//     <option value="A">A</option>
//     <option value="B">B</option>
//     <option value="C">C</option>
//     <option value="D">D</option>
// </select>

<select name="" id="" v-on:change="value = $event.target.value">
    <option value="A">A</option>
    <option value="B">B</option>
    <option value="C">C</option>
    <option value="D">D</option>
</select>

value: '', // A
```

#### 修饰符

* lazy：将 **input **转为 **change**
* number：转为数字
* trim：去除空白字符

### 自定义组件的v-model

```js
// 父组件
<heatmapChart v-model="newValue"></heatmapChart>

// 子组件
this.$emit('input', '我是子组件')
```

### .sync修饰符

> v-model 实现的双向数据绑定，父子组件没有明显的改动来源。故提出.sync修饰符

```js
// 父组件
<heatmapChart v-bind:value="newValue" v-on:update:value="newValue = $event"></heatmapChart>

// 子组件
props: {
    value: ''
}

this.$emit('update:value', '我是子组件')
```

提供了一种简写

```js
// 父组件
<heatmapChart v-bind:value.sync="newValue"></heatmapChart>
```



