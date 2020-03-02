# Promise

## 什么是Promise

es一种技术，解决异步回调，解决回调地狱

## 为什么要使用Promise

* promise是一个对象，对象和函数的区别就是对象可以保存状态，函数不可以（闭包除外）

* 并未剥夺函数return的能力，因此无需层层传递callback，进行回调获取数据

* 代码风格，容易理解，便于维护

* 多个异步等待合并便于解决

## 如何使用Promise

`fn().then();`

```js
new Promise(
  function (resolve, reject) {
    // 一段耗时的异步操作
    resolve('成功') // 数据处理完成
    // reject('失败') // 数据处理出错
  }
).then(
  (res) => {console.log(res)},  // 成功
  (err) => {console.log(err)} // 失败
)
```

## Promise原理是怎么实现的



