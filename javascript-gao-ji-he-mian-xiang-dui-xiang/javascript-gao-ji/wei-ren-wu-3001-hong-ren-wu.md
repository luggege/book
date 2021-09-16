### 宏任务

> 由宿主环境（执行JavaScript的环境，如浏览器、node）提供的，如setTimeout、setInterval

### 微任务

> 由语言标准（ECMA）提供的，如ES6的promise

### 执行机制

> js事件执行机制：从上往下执行，遇同步代码先执行**同步**代码，遇宏任务放到宏任务队列中，遇微任务放到微任务队列中；EventLoop轮询过程中会先检查微任务队列是否为空，不为空先执行**微任务队列**中的事件，否则才去执行**宏任务**中的事件，保证微任务永远在宏任务之前执行

```js
new Promise((resolve,reject) => {
// 同步
    setTimeout(() => {
    // 宏任务
        console.log(1);
        resolve()
    }, 10000)
}).then(() => {
// 微任务
    setTimeout( () => {
    // 宏任务
        console.log(2);
        // 微任务
        Promise.resolve(3)
            .then(x => console.log(x))
    }, 2000)
// 微任务
}).then(() => {console.log(4)})

// 1 4 2 3
```

分析：

* new Promise中的是同步代码，会先执行，等到10s后打印1后，在继续往下执行
* .then是微任务将里边的函数放到微任务队列中  \[setTimeout\]
* 在往下.then还是微任务，追加到微任务队列中 \[setTimeout，4\]
* EventLoop检查微任务队列，发现setTimeout是宏任务，放到宏任务队列【2，3】，此时微任务队列\[4\]
* EventLoop继续检查发现微任务队列中的4打印，微任务队列清空
* EventLoop执行宏任务队列，打印2，发现3 .then是微任务，加入到微任务队列中\[3\]，此时宏任务队列清空【】
* EventLoop检查到微任务队列不为空，执行微任务，打印3
* 到此微任务队列为空，宏任务队列为空，结束

### async/await

> async/await本质是基于promise的一些封装

```js
// 宏任务
setTimeout(_ => console.log(4))

async function main() {
// 同步
  console.log(1)
  await Promise.resolve()
  // 微任务
  console.log(3)
}

main()

console.log(2)

// 1 2 3 4
```

分析：

* async和await之间的代码同步执行，相当于new Promise传入的参数
* await之后的代码相当于.then传入的回调



