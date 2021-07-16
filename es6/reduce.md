### 数组的reduce方法

```js
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```

* callback 执行数组中每个值 \(如果没有提供 initialValue则第一个值除外\)的函数，包含四个参数

* * accumulator：累计器累计回调的返回值，它是上一次调用回调时返回的**累积值**，或initialValue
  * currentValue：数组中正在处理的元素
  * index（可选）：数组中正在处理的元素的索引。如果指定了initialValue，则起始索引为0，否则从1起始
  * array（可选）：调用reduce的数组
* initialValue（可选）：第一次调用callback的第一个参数。注意：在没有初始值的空数组上调用reduce会报错

返回值：返回函数累积处理的结果

