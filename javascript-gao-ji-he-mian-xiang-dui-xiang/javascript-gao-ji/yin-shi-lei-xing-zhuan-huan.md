### 隐式类型转换

```js
// 1. 字符串通过Number转为数字，进行比较
2 == '2'    // true

// 2. 布尔类型转为数值
0 == false  // true
'' == false // true  
'0' == false// true
'' == '0'   // false

// 3. null undefined 不进行转换
null == undefined // true

// 4. NaN
NaN == NaN  // false

// 5. Object转为Number或String，取决于另一个对比量的值
[] == 0     // false
[] == true  // false
[] == ![]   // true
```



