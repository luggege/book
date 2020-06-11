# Promise

## 什么是Promise

es一种技术，解决**异步回调**，解决**回调地狱**

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

```js
function Promise(executor){
    let that = this;
    that.status = 'pending';
    that.resolveValue = undefined;
    that.rejectValue = undefined;
    function resolve(value){
        if(that.status === 'pending'){
            that.status = 'resolved';
            that.resolveValue = value;
        }
    }
    function reject(value){
        if(that.status = 'pending'){
            that.status = 'rejected';
            that.rejectValue = value;
        }
    }
    // executor执行器
    executor(resolve, reject);
}

Promise.prototype.then = function(onFufiled, onRejected){
    let that = this;
    if(that.status === 'resolved'){
        onFufiled(that.resolveValue);
    }
    if(that.status === 'rejected'){
        onRejected(that.rejectValue);
    }
}
```

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

注意：

如果作为参数的Promise实例，自己定义了catch方法，被rejected之后，就不会触发Promise.all\(\)的catch方法，因为Promise实例的catch方法会返回一个新的promise，会继续调用then方法

```js
const p1 = new Promise((resolve, reject) => {
    resolve('hello')
})
.then(result => result)
.catch(e => e)

const p2 = new Promise((resolve, reject) => {
    throw new Error('error')
})
.then(result => result)
.catch(e => e)

Promise.all([p1, p2])
.then(result => console.log(result))
.catch(e => console.log(e))
// ["hello", Error: error]
```

如果p2没有catch方法，就会调用Promise.all\(\)的catch方法

```js
const p5 = new Promise((resolve, reject) => {
    resolve('hello')
})
.then(result => result)
.catch(e => e)

const p6 = new Promise((resolve, reject) => {
    throw new Error('error')
})
.then(result => {
    return result
})

Promise.all([p5, p6])
.then(result => console.log(result))
.catch(e => console.log(e))
// Error: error
```

### race\(\)

> 将多个Promise实例包装成一个新的Promise实例返回，用法同all\(\)，作用：将作为参数的Promise实例率先改变状态的值返回

```js
const promise1 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('p1'), 3000)
})
const promise2 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('p2'), 1000)
})
const promise3 = new Promise((resolve, reject) => {
    setTimeout(() => resolve('p3'), 2000)
})
Promise.race([promise1, promise2, promise3])
.then(result => console.log(result))
.catch(error => console.log(error))
Promise {<pending>}
// p2
```

### allSettled\(\)

> 用法同上，接受一组Promise实例，作用：等所有Promise实例状态都改变（不管成功还是失败），才会执行allSettled方法

### any\(\)

> 将多个promise实例，包装成一个promise实例

p的状态由p1、p2、p3决定

* p1、p2、p3有一个成功，p就成功

* p1、p2、p3都失败，p才失败

### resolve\(\)

> 将现有对象转为Promise对象，相当于Promise实例的resolve

```js
Promise.resolve('foo')
.then(result => console.log(result))
// foo

//等同于
new Promise(resolve => resolve('foo'))
.then(result => console.log(result))
// foo
```

### reject\(\)

> 相当于执行Promise实例的reject

```js
Promise.reject('error')
.catch(error => console.log(error))
// error

// 相当于
new Promise((resolve, reject) => {
    reject('error')
})
.then(null, error => console.log(error))
// error
```

## 应用

* 图片加载：加载完成调用resolve方法，改变Promise状态

```js
const imgLoad = (path) => {
    return new Promise((resolve, reject) => {
        const img = new Image()
        img.onload = resolve
        img.onerror = reject
        img.src = path
    })
}
```



