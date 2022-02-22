### Array.prototype.includes（ES2016）

> 返回一个布尔值，表示某个数组是否包含给定的值

```js
// 1.相当于indexOf，但是indexOf内部使用的是严格相等运算符进行判断，会对NaN造成误判
[1,2,NaN].includes(1)    // true
//[1,2,NaN].indexOf(NaN) // -1
[1,2,NaN].includes(NaN)  // true

// 2.第二个参数：查询的起始位置（默认为0，负数为表示倒数的位置，若大于数组长度重置为0）
[1,2,NaN].includes(2,1)  // true
[1,2,NaN].includes(2,-0) // true
[1,2,NaN].includes(2,-1) // false
[1,2,NaN].includes(2,-4) // true
```



