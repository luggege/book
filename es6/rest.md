### rest

> 接收余下参数

```js
function fn(a, ...rest) {
    console.log(a, rest, arguments)
    console.log(Array.prototype.slice.apply(arguments))
}
fn(2, 3)
// 2 [3] Arguments(2) [2, 3, callee: (...), Symbol(Symbol.iterator): ƒ]
// [2, 3]
```

#### rest和arguments的区别

* rest接收余下参数，且只能以...放在参数的最后
* rest是真正的数组，arguments是伪数组



