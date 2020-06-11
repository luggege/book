#### 局部自定义过滤器

```js
filters: {
  filter: value => {
      return value
  }
},
```

#### 全局自定义过滤器

```js
Vue.filter('filter', value => {
  console.log(value);
  return value
})
```

#### 使用

```js
<span>{{total | filter}}</span>
```

或者

```js
<span :title="total | filter">aaaaaa</span>
```



