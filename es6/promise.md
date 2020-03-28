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
new Promise(function (resolve, reject) {
    // 一段耗时的异步操作
    resolve('成功')   // 数据处理完成
    // reject('失败') // 数据处理出错
  }
).then(
    // resolved状态的回调函数
    res => console.log(res),  // 成功
    // rejected状态的回调函数
    err => console.log(err)   // 失败
)
```

## Promise原理是怎么实现的

### then\(\)

> 指定resolved和rejected状态的回调函数

Promise是一个构造函数，原型上也有then、catch、finally方法，.then\(\)方法返回一个**新的promise实例**，因此可以练式结构

### catch\(\)

> .then\(undefined,  rejection\)或.then\(null,  rejection\)的别名，即then的第二个回调函数，推荐写法，因为会捕获前边所有then方法的错误

用法同.then\(\)，用来捕获错误信息，同样返回一个promise实例，继续.then\(\)链式操作

```js
const someAsyncThing = function() {
  return new Promise(function(resolve, reject) {
    // 下面一行会报错，因为x没有声明
    resolve(x + 2);
  });
};

someAsyncThing()
.catch(function(error) {
  console.log('oh no', error);
})
.then(function() {
  console.log('carry on');
});
// oh no [ReferenceError: x is not defined]
// carry on
```

### finally\(\)

> 不管状态如何，成功与否，都会执行的操作

```js
new Promise(() => {}).finally(() => {})

//then方法的特例 等同于  
new Promise(function (resolve, reject) {
    // 一段耗时的异步操作
    resolve('成功')   // 数据处理完成
    reject('失败') // 数据处理出错
  }
).then(
    res => {return res},  
    err => {throw err}   
)
```

```js
Promise
.resolve()
.then(result => console.log(111))
.catch(error => console.log(222))
.finally(() => console.log(333))
// 111
// 333

Promise
.reject()
.then(result => console.log(111))
.catch(error => console.log(222))
.finally(() => console.log(333))
// 222 333
```

### all\(\)

> 将多个promise实例，包装成一个promise实例

p的状态由p1、p2、p3决定

* p1、p2、p3都成功，p才成功

* p1、p2、p3中有一个失败，p失败

```js
const p1 = new Promise(resolve => resolve('p1成功'))
const p2 = new Promise(resolve => resolve('p2成功'))
const p3 = new Promise(resolve => resolve('p3成功'))

const p = Promise.all([p1, p2, p3])
// Promise {<resolved>: Array(3)}
```

```js
const p6 = new Promise((resolve,reject) => reject('p6失败'))

const p = Promise.all([p1, p2, p3, p6]) 
// Uncaught (in promise) p6失败
```



