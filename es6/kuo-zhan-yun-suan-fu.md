# 扩展运算符

### 扩展运算符... 将数组转为用逗号分隔的参数序列。

```javascript
console.log(0, ...[1, 2, 3], 4)            // 0 1 2 3 4

console.log(...[])                         // undefined

// 只有函数调用的时候，扩展符才可以放到圆括号里
console.log((...[3]))                      // Uncaught SyntaxError: Unexpected number
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



