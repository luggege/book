### call\(\)和apply\(\)的作用与区别

> call和apply是Function.prototype的方法，所以每个function 实例都有这两个属性

* 相同点

* * 改变this指向

* 不同点
* * call的后边参数需要**逐个**列出来
  * apply的后边参数是一个**数组**

```js
function add(c, d){
    return this.a + this.b + c + d
}
var obj = {a: 1, b: 2};

add.call(obj, 3, 4)       // 1 + 2 + 3 + 4
add.apply(obj, [10, 20])  // 1 + 2 + 10 + 20
```



