# 扩展运算符

* 将**数组**转为用逗号分隔的参数序列

```javascript
console.log(0, ...[1, 2, 3], 4)            // 0 1 2 3 4

console.log(...[])                         // undefined

// 只有函数调用的时候，扩展符才可以放到圆括号里
console.log((...[3]))                      // Uncaught SyntaxError: Unexpected number
```

* 将**对象**的可遍历属性拷贝到当前对象中

```js
let z = {a: 1, b: 2}
let n = { ...z }

n // {a: 1, b: 2}

// 数组是特殊的对象
let foo = { ...['a', 'b', 'c'] }

 foo //{0: "a", 1: "b", 2: "c"}
```

### 替代函数的 apply 方法

```javascript
function fn(x, y, z) {
    console.log(x, y, z)
}
var args = [1, 2, 3]
fn.apply(null, args)

// ES6简洁写法
fn(...args)

var arr1 = [1, 2, 3];
var arr2 = [4, 5, 6];
Array.prototype.push.apply(arr1, arr2)
arr1.push(...arr2)
```



