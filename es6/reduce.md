### 数组的reduce方法

```js
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

* callback 执行数组中每个值 \(如果没有提供 initialValue则第一个值除外\)的函数，包含四个参数

* * accumulator：累计器累计回调的返回值，它是上一次调用回调时返回的**累积值**，或**initialValue**
  * currentValue：数组中正在处理的元素
  * index（可选）：数组中正在处理的元素的索引。如果**指定了initialValue**，则**起始索引为0**，否则**从1起始**
  * array（可选）：调用reduce的数组
* initialValue（可选）：第一次调用callback的第一个参数。注意：在**没有初始值**的**空数组**上调用reduce会**报错**

返回值：返回函数累积处理的结果

```js
[1, 2, 3, 4].reduce(
    (accumulator, currentValue, index, array) => {
        console.log(accumulator, currentValue, index, array)
        return accumulator + currentValue
    }
)
// 1 2 1 (4) [1, 2, 3, 4]
// 3 3 2 (4) [1, 2, 3, 4]
// 6 4 3 (4) [1, 2, 3, 4]
```

```js
[1, 2, 3, 4].reduce(
    (accumulator, currentValue, index, array) => {
        console.log(accumulator, currentValue, index, array)
        return accumulator + currentValue
    }
, 10)
// 10 1 0 (4) [1, 2, 3, 4]
// 11 2 1 (4) [1, 2, 3, 4]
// 13 3 2 (4) [1, 2, 3, 4]
// 16 4 3 (4) [1, 2, 3, 4]
```

```js
// 1.没有初始值的空数组调用reduce，会报错
[].reduce((accumulator, currentValue, index, array) => accumulator + currentValue)
// VM698:1 Uncaught TypeError: Reduce of empty array with no initial value

// 2.数组只有一个元素且没有初始值或者只有初始值的空数组，不会执行callback
[3].reduce((accumulator, currentValue, index, array) => accumulator + currentValue)
[].reduce((accumulator, currentValue, index, array) => accumulator + currentValue， 3)
// reduce() 没有初始值
var maxCallback = ( acc, cur ) => Math.max( acc.x, cur.x );
[ { x: 2 }, { x: 22 }, { x: 42 } ].reduce( maxCallback ); // NaN
[ { x: 2 }, { x: 22 }            ].reduce( maxCallback ); // 22
[ { x: 2 }                       ].reduce( maxCallback ); // { x: 2 }
[                                ].reduce( maxCallback ); // TypeError
// 所以最好指定初始值
[ { x: 2 }, { x: 22 }, { x: 42 } ].reduce( (accumulator, currentValue) => Math.max(accumulator, currentValue.x), 0 );  // 42
```



